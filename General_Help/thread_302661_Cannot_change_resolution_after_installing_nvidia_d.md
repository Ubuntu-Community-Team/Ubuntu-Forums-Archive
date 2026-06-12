---
title: "Cannot change resolution after installing nvidia drivers"
date: 2006-11-19
forum: General Help
---

### Post by s10n on 2006-11-19
Hi, after installing the nvidia drivers and restarting the computer, my resolution changes to 640x480 and thats the only one that shows on the list, so I'm stucked on this resolution. I tried to reconfigure the x server or something like that with a command I  found on another post and now ubuntu doesnt boot, I would like to know how I can or why I cant change my resolution. Thanks.

---

### Post by bettlebrox on 2006-11-19
Post your /etc/X11/xorg.conf

---

### Post by BLTicklemonster on 2006-11-19
Try

sudo apt-get install nvidia-settings

then 

sudo nvidia-settings

and try the second option down and set your resolution where you want it and save to xorg.conf and see if that does it.

---

