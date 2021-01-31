## Sleepy Pi 2 sketchbook directory for AQM devices

Sleepy Pi 2 Software Jumper

The Power Bypass can alternatively be enabled in software via an i2c GPIO chip. This is independent of the Arduino so is not effected by code upload. To access this chip from the Raspberry Pi, first ensure that the i2c tools are installed.

To see the i2c devices:
```
sudo i2cdetect -y 1
```
The device at address 0x24 is the GPIO chip and the 0x68 is the Real Time Clock.


To switch the Software Jumper ON type:
```
i2cset -y 1 0x24 0xFD
```


to switch the Software Jumper OFF (power on default) type:
```
i2cset -y 1 0x24 0xFF
```
CAUTION if you remove the software jumper without the Arduino having “taken over” control of the power via your program, it will unceremoniously cut the power to the Raspberry Pi – NOT do a controlled shutdown.
