---
title: "Ubuntu 13.10 keyboard issue"
date: 2014-01-30
forum: General Help
---

### Post by linusstruyk on 2014-01-30
Hello,

I just installed Ubuntu on my laptop, I'm using an external keyboard/mouse/monitor.
When my laptop suspends itself(sleepmode), it's not possible to wake it up from the sleep mode by just pressing the keyboard/mouse(like in windows..)

I read these 2 threads: [http://ubuntuforums.org/showthread.php?t=1857062&highlight=usb0](http://ubuntuforums.org/showthread.php?t=1857062&highlight=usb0) and [http://ubuntuforums.org/showthread.php?p=4466270](http://ubuntuforums.org/showthread.php?p=4466270)

This is how it looks for me.
cat /proc/acpi/wakeup
> Device    S-state      Status   Sysfs node
P0P1      S4    *disabled  pci:0000:00:1e.0
USB0      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *enabled   pci:0000:00:1d.1
USB2      S3    *enabled   pci:0000:00:1d.2
USBR      S3    *enabled   pci:0000:00:1d.3
EHC1      S3    *enabled   pci:0000:00:1d.7
USB3      S3    *enabled   pci:0000:00:1a.0
USB4      S3    *enabled   pci:0000:00:1a.1
USB5      S3    *disabled
EHC2      S3    *enabled   pci:0000:00:1a.7
HDEF      S3    *disabled  pci:0000:00:1b.0
PXSX      S5    *enabled   pci:0000:02:00.0
GLAN      S5    *disabled
LID0      S3    *enabled 
SLPB      S3    *enabled 


And as far as i can see, using the lsusb command

> Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



Usb2 is my keyboard(dell keyboard), and it's enabled.

Any ideas?

---

