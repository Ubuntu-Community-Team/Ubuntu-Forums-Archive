---
title: "Lock screen changed to the old style -Ubuntu 16.04-"
date: 2016-08-28
forum: General Help
---

### Post by irubs09 on 2016-08-28
Hi! I use Ubuntu 16.04 (Unity) on my Dell Inspiron-20-Model-3043 (touch screen).

My problem is that the lock screen (ctrl + alt + L) changed to the old style like the one in Ubuntu 10.10, and I don't know why exactly, I don't remember have done anything in particular.
maybe it changed after the installation of Unity 8 mir but I didn't notice it until 3 days later so I'm not sure. Something curious is that the login screen works perfectly

These are the commands I tried until now: 

 sudo dpkg-reconfigure lightdm
 sudo service lightdm restart
 sudo lightdm

But nothing works, and actually I'm not sure if LightDM controls also the lock screen or only the login screen

---

### Post by deadflowr on 2016-08-29
*Thread moved to **General Help**.* 

I believe the lock screen is part of the gnome-screensaver package setup.

---

### Post by irubs09 on 2016-09-01
Ok I solved it, fallowing these steps:

1) Go to settings
2) Go to accessibility
3) Uncheck "on-screen keybord"

Now my lock screen is back to normal

---

### Post by inalmada on 2017-02-07
> **irubs09 said:**
> Ok I solved it, fallowing these steps:

1) Go to settings
2) Go to accessibility
3) Uncheck "on-screen keybord"

Now my lock screen is back to normal

Thanks a lot you saved my day !

---

