---
title: "Changing default gamma settings"
date: 2008-04-23
forum: General Help
---

### Post by UncertainGod on 2008-04-23
Hi all, I use a pretty old CRT monitor on my Ubuntu machine and by default the screen is very dark, I know that I can change this by using xgamma in the terminal but every time the screensaver comes on it gets reset back to it's default value.

Could someone point out where I can change the default gamma value please?

---

### Post by y-lee on 2008-04-23
I think you should be able to set the gamma value  in the file **/etc/X11/xorg.conf** in the Monitor section, see [[COLOR="RoyalBlue"]_xorg.conf - Configuration File for Xorg_[/COLOR]]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html").

Note edit this file you must open it as superuser. Copy and paste the below code in a terminal to edit this file:

```
gksudo gedit /etc/X11/xorg.conf
```

Note it would be wise to backup this file first before you edit it and to be very careful. The change should take effect next time you reboot.

---

### Post by UncertainGod on 2008-04-24
Thanks for the info, I'm sure that will prove to be a useful bookmark in the future as well.

---

### Post by avi_b on 2009-06-30
try $xgamma -gamma 0.8
change the value to suit your screen

---

