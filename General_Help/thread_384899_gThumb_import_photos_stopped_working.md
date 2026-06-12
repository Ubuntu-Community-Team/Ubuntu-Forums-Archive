---
title: "gThumb import photos stopped working"
date: 2007-03-15
forum: General Help
---

### Post by tino27 on 2007-03-15
I've been using the automatic gThumb photo import for my two PTP mode cameras for a few months on Edgy with no problems. Now I get 

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I suppose it could be due to an update, but what I would guess would be something related to the installation of a Brother MFC device. That involved adding an LPR driver, CUPS driver and SANE driver. Additionally, the following line was added to 45-libsane.rules in /etc/udev:

> SYSFS{idVendor}=="04f9", MODE="666", GROUP="scanner"

I've tried removing the above line, and unplugging all USB devices except the camera and my mouse, and I still get the same error. I see the appropriate lines in 45-libgphoto2.rules for the cameras, and I don't notice any processes that look like they'd conflict. Any ideas?

---

### Post by yabbadabbadont on 2007-03-15
Does no one search anymore?   :D

[http://www.ubuntuforums.org/showthread.php?t=384745](http://www.ubuntuforums.org/showthread.php?t=384745)

---

### Post by tino27 on 2007-03-15
Yikes, I did do a search, but somehow missed that one. Thanks so much for the help.

---

