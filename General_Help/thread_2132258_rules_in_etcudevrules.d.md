---
title: "rules in /etc/udev/rules.d"
date: 2013-04-04
forum: General Help
---

### Post by jardag on 2013-04-04
jardag@precise-GiB:~$ lsusb
Bus 001 Device 006: ID 15ba:002a Olimex Ltd. ARM-USB-TINY-H JTAG interface
jardag@precise-GiB:~$ cd /dev/bus/usb
crw-rw-r-- 1 root root 189, 0 Apr  4 21:13 001
crw-rw-r-- 1 root root 189, 5 Apr  4 21:13 006
jardag@precise-GiB:/dev/bus/usb/001$ cat /etc/udev/rules.d/40*
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0x15ba", ATTRS{idProduct}=="0x002a", MODE="0660", GROUP="lp"
Why the mode and group of the 006 did not change ?

---

