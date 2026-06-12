---
title: "tty terminal sessions aren't visible?"
date: 2013-10-17
forum: General Help
---

### Post by dannyboy79 on 2013-10-17
I am running Xubuntu 12.04.3 with an Nvidia 8400GS on a 26" HDTV hooked up via VGA. I was going to upgrade my Nvidia Driver to 319.60 but when I try to go to one of my terminal consoles all I can see is a black screen. I have checked that they are there with ps aux | grep tty
```
root      1119  0.0  0.0  20008   196 tty4     Ss+  Oct06   0:00 /sbin/getty -8 38400 tty4
root      1125  0.0  0.0  20008   196 tty5     Ss+  Oct06   0:00 /sbin/getty -8 38400 tty5
root      1169  0.0  0.0  71360  1692 tty2     Ss+  Oct06   0:00 /bin/login --       
root      1170  0.0  0.0  20008   196 tty3     Ss+  Oct06   0:00 /sbin/getty -8 38400 tty3
root      1172  0.0  0.0  71360  1708 tty6     Ss+  Oct06   0:00 /bin/login --       
root      1367  0.0  0.0  20008   296 tty1     Ss+  Oct06   0:00 /sbin/getty -8 38400 tty1
root      1369  1.2  1.8 185300 37604 tty7     Ss+  Oct06 200:27 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
```
Does anyone know why it's just a black screen and not showing me the option to log in textually? Any help would be appreciated.

---

