---
title: "[SOLVED] kernel 2.6.24-19-generic broke my X-server"
date: 2008-06-23
forum: General Help
---

### Post by jimbob on 2008-06-23
I took the new kernel upgrade along with associated modules this morning but it will not run anything but 800x600 resolution.  It appears that I have everything necessary installed including the appropriate linux restricted modules.  I have tried to regenerate the xserver to no avail.

AMD Athlon 3400+ Sempron
Nvidia GeForce 6600GT graphics
Acer AL2416W 1920x1200 resolution

---

### Post by TeoBigusGeekus on 2008-06-23
Switch to the previous kernel and wait for an update...

---

### Post by jimbob on 2008-06-27
Here is a fix that worked for me. Boot up your system in whatever mode it starts in (mine was using 640x480, UGH!) and install envyng-core and envyng-glx. Start envyng-glx in a terminal as root, click on Nvidia and apply and let it do its thing. Mine deleted nvidia-glx-new and nvidia-settings and then installed (re-installed?) a bunch of stuff and asked me to reboot which I did and voila! - worked like a charm.

---

