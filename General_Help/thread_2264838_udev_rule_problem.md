---
title: "udev rule problem"
date: 2015-02-10
forum: General Help
---

### Post by dtree46 on 2015-02-10
The following udev rule in /etc/udev/rules.d/51-android.rules does not work.
I'm having trouble finding out why.
Any help appreciated.

Get same error as user also.
root@dlw-HP:/home/dlw# adb devices
List of devices attached 
????????????    no permissions

Here is the udev rule.
# LG VS930
SUBSYSTEM=="usb", SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6218", MODE="0666", GROUP="plugdev"

root@dlw-HP:/home/dlw# lsusb
Bus 001 Device 004: ID 046d:0821 Logitech, Inc. HD Webcam C910
Bus 001 Device 005: ID 1004:6218 LG Electronics, Inc

---

