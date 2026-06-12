---
title: "Lag in Firefox"
date: 2006-12-30
forum: General Help
---

### Post by taekwondodogoof on 2006-12-30
Hi,
     I've had to switch to Vesa recently in Xserver, however, when I go around firefox and I scroll down, I can see it refresh from the bottom down, like in slow motion. I've tried changing back to nv drivers. See, the reason I had to change was because I got a Geforce 8800 GTX, however, nv wouldn't start after that. So, is there any suggestions to fix this without having to go through xserver? Thanks =D

PS I think it may have something to do with the fact that my LCD monitor has a refresh rate of 60 but Ubuntu is stuck at 85, and I can't change it

---

### Post by taurus on 2006-12-30
Change to vesa and then follow this guide to install nVidia driver for your card...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by taekwondodogoof on 2006-12-30
Hmm.. I did what it said, then I reconfigured the xserver, but when I rebooted under nv it said that xserver was not configured properly.

---

### Post by taurus on 2006-12-30
After you installed nvidia-glx, you should switch to "nvidia" driver instead of "nv" driver in /etc/X11/xorg.conf!!!

---

### Post by taekwondodogoof on 2006-12-30
Ohhh.. sorry!! I'll try again... thanks for putting up with me, you're a great help!

---

### Post by taurus on 2006-12-31
Check out this thread especially my reply, #5.  Don't feel like typing the whole thing over again...  ;) 

[http://www.ubuntuforums.org/showthread.php?t=328499](http://www.ubuntuforums.org/showthread.php?t=328499)

---

### Post by taekwondodogoof on 2006-12-31
Wait.. I did all of that, however, when I configured xserver for nvidia, I rebooted and the nvidia splash popped up, then vertical green lines appeared running up and down the screen and didn't go away. So I had to revert back to vesa

---

### Post by taurus on 2006-12-31
Boot into recovery mode from GRUB menu and at the prompt, run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```
Now, what happens?

---

### Post by taekwondodogoof on 2006-12-31
Wait.. should I change back to nvidia before doing so?

---

### Post by taurus on 2006-12-31
If you want to...

```

dpkg-reconfigure -phigh xserver-xorg
nvidia-xconfig
startx
```

---

### Post by taekwondodogoof on 2006-12-31
after using startx, I get IO error 104

---

