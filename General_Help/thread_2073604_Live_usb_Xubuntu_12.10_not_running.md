---
title: "Live usb Xubuntu 12.10 not running"
date: 2012-10-19
forum: General Help
---

### Post by yurfader on 2012-10-19
I tried to run Xubuntu 12.10 to a Gateway LT4004u  through a live usb without success. The startup ends with an error and it only displays the terminal. I was able to copy the Xorg.0.log file and the last part of the file is the following:

> 
[    65.879]     compiled for 1.12.99.902, module version = 0.4.3
[    65.879]     Module class: X.Org Video Driver
[    65.879]     ABI class: X.Org Video Driver, version 13.0
[    65.879] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    65.880] (II) VESA: driver for VESA chipsets: vesa
[    65.880] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    65.880] (II) FBDEV: driver for framebuffer: fbdev
[    65.881] (--) using VT number 8

[    65.889] (II) intel(0): using device path '/dev/dri/card0'
[    65.889] (WW) Falling back to old probe method for vesa
[    65.889] (WW) Falling back to old probe method for modesetting
[    65.890] (WW) Falling back to old probe method for fbdev
[    65.890] (II) Loading sub module "fbdevhw"
[    65.890] (II) LoadModule: "fbdevhw"
[    65.890] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    65.891] (II) Module fbdevhw: vendor="X.Org Foundation"
[    65.891]     compiled for 1.13.0, module version = 0.0.2
[    65.891]     ABI class: X.Org Video Driver, version 13.0
[    65.891] (EE) intel(0): [drm] Failed to detect GEM.  Kernel 2.6.28 required.
[    65.891] (EE) intel(0): Failed to become DRM master.
[    65.891] (II) UnloadModule: "intel"
[    65.891] (EE) Screen(s) found, but none have a usable configuration.
[    65.891] 
Fatal server error:
[    65.891] no screens found
[    65.891] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    65.892] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    65.892] (EE) 
[    65.909] Server terminated with error (1). Closing log file.

Any help would be really appreciated.

---

### Post by 2F4U on 2012-10-20
What is your graphics card? There seems to be a problem with it. It looks as if it tries to load the intel driver but somehow fails.

---

### Post by yurfader on 2012-10-20
It is the GMA 3600, it was supposed to be supported by the linux kernel 3.5. In Ubuntu 12.04 it was working but without graphics acceleration.


It is not supported then in this version of (X)ubuntu?

:(

---

### Post by Riccardoc on 2012-10-20
Same thing with standard Ubuntu; this is a regression from 12.04, which at least booted in 800x600.
Also it is strange that it doesn't work, since 3.4+ kernel actually supports GMA 3600...

---

### Post by yurfader on 2012-10-20
Then we should not expect any support to the GMA 3600 card from ubuntu?

:(

---

### Post by Nordicnurse on 2012-10-20
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1069031](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1069031)

---

