---
title: "Trying to program Arduino with a bluetooth serial shield ... and failing"
date: 2015-10-03
forum: General Help
---

### Post by rdragonrydr on 2015-10-03
Hello everyone.

I just bought a Adafruit Bluefruit programmer shield, which is a variable speed bluetooth serial shield that stacks on the Arduino and allows for wireless programming with no new software or drivers needed. Theoretically.
It works with everyone's least favorite Microsoft OS, and allegedly Macs, but Linux support varies. It seems not to work for me, and I was told it was some kind of thing with the bluetooth stack, and differences between Linux and other OSes.


To set it up, I paired it with Blueman, and then ran sudo (running as regular user failed) rfcomm bind 0 <device's mac address>.
It shows up as a valid port in the IDE, and I can send and receive data using the serial communication monitor, but its stated purpose, actually programming the arduino, fails.
It returns "stk_500()" error and "Programmer not responding" and "out of sync" errors when attempting to program. Once or twice I got a "incorrect speed" error, but this seems to be rare.

It resets the arduino on connection and everything, but it just won't program it. Does anyone know of any steps I am missing, bugs with the stack or blueman or rfcomm, or some other odd problem here?
Supposedly, some other devices work fine with Ubuntu, but this one isn't. Is there some kind of odd signal that gets sent when the Arduino is supposed to start being programmed that might be getting blocked?

I have been told that there is nothing special about the shield that would make it act differently compared to some homemade HC_06 shield, but I may be wrong.

---

### Post by rdragonrydr on 2015-10-04
Actually, I got it solved. Follow these instructions to get a bluetooth serial device connected. It is especially relevant when working with Arduino.

See [http://playground.arduino.cc/Learning/ArduinoBT-Ubuntu](http://playground.arduino.cc/Learning/ArduinoBT-Ubuntu) for details.

---

### Post by rdragonrydr on 2015-10-13
Actually, could someone please help me? It turns out that it only worked the once. I never got it to work again. It seems to not be changing baud rate when the IDE switches to programming mode. The arduino resets, but the serial data is out of sync because the shield stays at some baud rate (I think 9600 is default) when it should change to 115200 baud. It works fine with Windows and Mac, and needs no drivers on either. How can I tell a device to switch baud rate, and does support for this even exist?

---

