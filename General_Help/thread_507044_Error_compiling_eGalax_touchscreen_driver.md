---
title: "Error compiling eGalax touchscreen driver"
date: 2007-07-22
forum: General Help
---

### Post by JeyKey on 2007-07-22
I am trying to set up a touchscreen, but for some reason, I cant get the evtouch module to function properly. The touchscreen does work, but the Y-axis is inverted, and it needs some calibration. 

excerpt from xorg log:
> (II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input/evtouch_drv.so
dlopen: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/xorg/modules/input/evtouch_drv.so)
(EE) Failed to load /usr/lib/xorg/modules/input/evtouch_drv.so
(II) UnloadModule: "evtouch"
(EE) Failed to load module "evtouch" (loader failed, 7) 

according to lsusb, it's an eGalax touchscreen, found at /dev/input/event2. I've also tried the driver from the manufacturer, but it wont compile. I actually got the touchscreen to work on another computer, which runs ubuntu 2.6.20-16 Xorg 7.2, whereas this one is running Debian 2.6.18-4 Xorg 7.1. Since I already know that the evtouch driver should work, I haven't focused much on the driver from the manufacturer.

Is anyone able to make sense of the xorg log file? It's not even my own computer, but a friend's - and he needs it back in about a week.

Thanks in advance!

---

