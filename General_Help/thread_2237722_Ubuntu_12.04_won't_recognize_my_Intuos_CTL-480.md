---
title: "Ubuntu 12.04 won't recognize my Intuos CTL-480"
date: 2014-08-03
forum: General Help
---

### Post by Kurushimi on 2014-08-03
I don't understand what the problem could be. I followed the instructions to install it from here: [http://sourceforge.net/projects/linuxwacom/?source=dlp](http://sourceforge.net/projects/linuxwacom/?source=dlp)

But I plug it in and pressing it does absolutely nothing. 

I install input-wacom-0.22.1 from the tarball and xf86-input-wacom-0.25.0 from the tarball. I followed the instructions they had written on the wiki for the installation (even though they were somewhat different than the instructions given in the INSTALL file in the folders themselves, which is pretty confusing). I don't know where I messed up but every time I google it, the responses claim it should work after I install these things, but it still isn't working at all.

When I run "lsusb | grep Wacom" it shows that the wacom device is detected. When I run "xinput list" the wacom device is nowhere to be found. I'm not really sure what this means but I think that may be a problem.

Edit: I tried to go through the installation one more time after uprgrading my linux kernel version from version 2.6.38 to version 3.7. Now when I plug in the device, the screen goes black and there's nothing I can do.

---

