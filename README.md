# VL53L0X driver for the raspberry pico sdk in cpp

adapted from the arduino version @ [pololu/vl53l0x-arduino](https://github.com/pololu/vl53l0x-arduino)

## Usage

```cpp
#include "VL53L0X.h"

#define I2C_SDA 8
#define I2C_SCL 9

// ...

// Initialize I2C0 at 400kHz
i2c_init(i2c0, 400 * 1000);
gpio_set_function(I2C_SDA, GPIO_FUNC_I2C);
gpio_set_function(I2C_SCL, GPIO_FUNC_I2C);
gpio_pull_up(I2C_SDA);
gpio_pull_up(I2C_SCL);

// Initialize VL53L0X sensor
VL53L0X sensor;
sensor.init();
sensor.setTimeout(500);

// Start continuous back-to-back mode (take readings as fast as possible)
sensor.startContinuous();

// ...

printf("millimeters: %d", sensor.readRangeContinuousMillimeters());
```
