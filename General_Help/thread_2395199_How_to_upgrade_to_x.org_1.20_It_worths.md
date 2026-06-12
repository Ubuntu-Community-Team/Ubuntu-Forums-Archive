---
title: "How to upgrade to x.org 1.20? It worths?"
date: 2018-06-28
forum: General Help
---

### Post by nachazo on 2018-06-28
Hi!
I just saw new X.org 1.20 is out, but I have not a clue on how to upgrade it. Actually I have:

```
inxi -G
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.02hz, 1280x1024@60.02hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop version: 4.5 Mesa 18.0.0-rc5
```

It's on 18.04 Ubuntu.
Worths upgrade?

I'm experiencing issues when trying to connect with VNC and my display are powered off... first I wanna try if 1.20 solves...

Thanks!!

---

### Post by mc4man on 2018-06-28
You could wait for it to show up in 18.10 & try there (probably some point in july)
Otherwise you'd need to package build the xserver-xorg-core source & replace all current 1.19 installed packages with 1.20 packages.
Seems possible though couldn't say if there would be any issues though see the diff - 

```
$ inxi -G
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 755M]
           Display Server: x11 (X.Org 1.20.0 )
           drivers: modesetting [COLOR="#FF0000"]FAILED[/COLOR]: fbdev,vesa,nouveau
           Resolution: 1920x1080@59.91hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile
           version: 4.5 Mesa 18.0.0-rc5

```
```
~$ inxi -G
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK107M [GeForce GT 755M]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting,nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@59.91hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile
           version: 4.5 Mesa 18.0.0-rc5
```

Best to wait for Ubuntu to offer, if any better it would be available for 18.04 in Dec (proposed) or next Feb. as HWE packages.

---

### Post by nachazo on 2018-06-29
Will wait [COLOR=#000000]mc4man, thanks for answer!

I will open another post to ask for help with my problem.[/COLOR]

---

