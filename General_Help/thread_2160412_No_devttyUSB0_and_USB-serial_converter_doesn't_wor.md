---
title: "No /dev/ttyUSB0 and USB-serial converter doesn't work"
date: 2013-07-07
forum: General Help
---

### Post by Maheriano on 2013-07-07
Hi, I've been running Heyu and X10 for home automation on my machine for years but I haven't touched it in the last year or so. Today I hooked it up again and tried to access it by running```
heyu start
```but it gave me an error: ```
deemar@Chugger:/dev/usb$ heyu start
starting heyu_relay
HEYU: Can't open tty line.  Check the permissions.

```I even run it as sudo and it gives me the same error. So I ran```
ls -l /dev/ttyUSB0
```to figure out what the permissions are and there is no /dev/ttyUSB0. I got a listing of all /dev devices and there isn't any ttyusb at all. There are a bunch of ttyS* and there is a usb directory but no ttyUSB*. Did this change recently? How do I access this CM11A device I use for X10? When I run lsusb with it plugged in or not plugged in, I get the same response: ```
deemar@Chugger:/dev/usb$ lsusb
Bus 003 Device 003: ID 0603:8120 Novatek Microelectronics Corp. 
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```
What's going on here?

---

### Post by Maheriano on 2013-07-07
Nevermind. The USB cable wasn't plugged into the converter. Works now.

---

