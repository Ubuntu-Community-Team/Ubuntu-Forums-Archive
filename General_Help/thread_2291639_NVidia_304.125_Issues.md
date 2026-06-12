---
title: "NVidia 304.125 Issues"
date: 2015-08-21
forum: General Help
---

### Post by XWindowWasher on 2015-08-21
New to Linux, learning on an older PC. So far very happy except for one thing...

NVIDIA 7300LE on Seki 50" TV as monitor, when switching to 1920x1080 resolution screen artifacts/tearing occurs. The nouveau driver(module?) does not have this issue, but, Kodi crashes with nouveau.

I have tried:
-Different Linux 'flavors': Mint, LinuxLite, Zorin, etc.
-Drivers: nvidia-current, from Nvidia site, versions 304 - 340(following specific Ubuntu instructions, remove nouveau etc.)
-XOrg configurations using output from xrandr, cvt(?) and many suggestions from many sites found through Google.

I'm guessing this is a setting somewhere or a conflict. The hardware seems to be OK as the nouveau driver does not have an issue.

Thanks in advance!

---

### Post by oldfred on 2015-08-21
That is an old nVidia card.
It is only supported by the legacy driver 304.xx.
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If you install a newer driver it may create issues. And you have to totally purge any other driver from nVidia if you have installed the incorrect one. They do not easily replace/update. And you should only install from Ubuntu repository.

Lets see what is installed now:

 #What is installed
dkms status

---

