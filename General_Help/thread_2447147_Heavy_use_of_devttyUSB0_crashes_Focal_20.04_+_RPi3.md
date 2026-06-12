---
title: "Heavy use of /dev/ttyUSB0 crashes Focal 20.04 + RPi3"
date: 2020-07-13
forum: General Help
---

### Post by carlos-tangerino on 2020-07-13
The system
Using RPi V3B V1.2, Focal 20.04
USB to serial with ftdi driver.

A simple Python program like
[COLOR=#CC7832]import [/COLOR]minimalmodbus

instrument = minimalmodbus.Instrument([COLOR=#6A8759]'/dev/ttyUSB0'[/COLOR][COLOR=#CC7832], [/COLOR][COLOR=#6897BB]2[/COLOR])
instrument.debug = [COLOR=#CC7832]False
[/COLOR]instrument.serial.baudrate = [COLOR=#6897BB]9600
[/COLOR]instrument.serial.timeout = [COLOR=#6897BB]1
[/COLOR][COLOR=#CC7832]while True[/COLOR]:
    instrument.read_long([COLOR=#6897BB]229[/COLOR])


Crashes the system (see images bellow). 
**The same does not happen if I use /dev/ttyAMA0 port**

Using the terminal I got:


[IMG]https://user-images.githubusercontent.com/3164100/87328094-5d5e6180-c50b-11ea-8dbb-476b5ec1b853.png[/IMG]

And later....

[IMG]https://user-images.githubusercontent.com/3164100/87328057-50417280-c50b-11ea-9ba2-6709db522ffb.png[/IMG]

---

