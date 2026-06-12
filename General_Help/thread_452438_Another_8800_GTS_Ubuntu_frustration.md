---
title: "Another 8800 GTS Ubuntu frustration"
date: 2007-05-23
forum: General Help
---

### Post by Miguelone on 2007-05-23
Hey guys,

Im sure this has been covered a hundred times in the forums. I've done my research and ive even printed 10 pages worth of tuturial from the forums.

I even installed Envy but still no luck.  I cannot get 3d accelleration from the nvidia drivers.

Ive been trying to install it on Feisty all this time. Will the 8800GTS work with the Ubuntu 6.04?

Or if anyone knows of a new work around on this pls guide me through. I am new to Ubuntu its been about 2 weeks for me but im comfy with the terminal from all the tutorials ive gone through.

thnx all. If i could solve this it would really boost my confidence in staying with this OS.

---

### Post by angryfirelord on 2007-05-23
Go to your x.org and under Driver, make sure it says "nvidia" (if you haven't done that already).

Otherwise, I'd try the beta driver from nvidia.

---

### Post by Frickalik on 2007-05-23
I would just like to point out that i have a 8800 GTS and i used the 7.04 Desktop CD. ANd it ran perfect. I installed the Driver before i installed Ubuntu and when it finished installing. everything ran fine ;)

---

### Post by desertboy on 2007-05-27
Mine wouldn't boot, I had to boot 6.10 edgy which failed to start the xserver. (Fiesty wouldn't boot at all.) then edit /ec/X11/xorg.conf

change Driver "nv"   to Driver "vesa"

then startx

It then starts up in 1280x1024 which is annoying, but you can install it and then install the new nvidia drivers.

---

