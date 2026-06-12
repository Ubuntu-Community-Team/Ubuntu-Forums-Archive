---
title: "Preparing Restricted Drivers &quot;Failed&quot; during start up"
date: 2006-11-18
forum: General Help
---

### Post by Al3xanR0 on 2006-11-18
I haven't given up yet, someone will help me. 

I have been struggling with Nvidia, XGL, Beryl my post seem to go unanswered thus far. As I continue to search for possible root causes I have come across another potential peice to the puzzle. I noticed that when power up the laptop, particularly when services are loading -Preparing Restricted Drivers "Failed" scrolls up the LCD during start up. I thought that it was note worthy to mention in light of the failure loading nvidia-kernel-modules as noted in a excerpt from /var/log/Xorg.0.log

> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

However, a quick ```
dpkg -l | grep nvidia
``` and ```
dpkg -l | grep linux-restricted-modules
```

 reveals the following installed nvidia packages and linux-restricted-modules

> ii  nvidia-glx                             1.0.8776+2.6.15.12-1                   NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-glx-dev                         1.0.8776+2.6.15.12-1                   NVIDIA binary XFree86 4.x/X.Org driver devel
ii  nvidia-kernel-common                   20051028+1                             NVIDIA binary kernel module common files
rc  nvidia-settings                        1.0-3ubuntu7                           Tool of configuring the NVIDIA graphics driv
> ii  linux-restricted-modules-2.6.15-27-686 2.6.15.12-1                            Non-free Linux 2.6.15 modules on PPro/Celero
ii  linux-restricted-modules-686           2.6.15.25                              Restricted Linux modules on PPro/Celeron/PII
ii  linux-restricted-modules-common        2.6.15.12-1                            Non-free Linux 2.6.15 modules helper script


So where do we go from here or will this be yet another unanswered post?

---

