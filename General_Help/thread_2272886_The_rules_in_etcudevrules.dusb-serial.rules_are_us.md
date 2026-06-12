---
title: "The rules in /etc/udev/rules.d/usb-serial.rules are useless ?"
date: 2015-04-09
forum: General Help
---

### Post by eduard-budai on 2015-04-09
Hello to everyone. :smile:

During the last weeks I've spent many days searching the Web and trying  many solutions without any luck for the following problem: 

I have two USB adapters connected to a computer and at each boot they  are randomly assigned as /dev/ttyUSB0 and /dev/ttyUSB1, although I've  tried many rules in /etc/udev/rules.d/usb-serial.rules, considering the  informations gathered by running udevadm info -a -n - but nothing seems  to work.

lsusb gives:

Bus 003 Device 002: ID 0557:2008 ATEN International Co., Ltd UC-232A Serial Port [pl2303]
Bus 002 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

I've created a file in /etc/udev/rules.d/usb-serial.rules with the following content:

KERNEL=="ttyUSB*", DRIVER=="ftdi_sio", NAME="ttyUSB0"
KERNEL=="ttyUSB*", DRIVER=="pl2303", NAME="ttyUSB1"

dmesg | grep ttyUSB gives:

[   14.559649] usb 3-1: pl2303 converter now attached to ttyUSB0
[   14.615811] usb 2-1: FTDI USB Serial Device converter now attached to ttyUSB1

What I need is that the FT232 adapter is always /dev/ttyUSB0 and the UC-232A adapter is always /dev/ttyUSB1.

Attached are  the outputs of udevadm info -a -n for /dev/ttyUSB0 and /dev/ttyUSB1.

---

