---
title: "Screen Resolution - Now Won't Display"
date: 2008-05-20
forum: General Help
---

### Post by Amnesia180 on 2008-05-20
Hi All,

I have tried setting my screen resolution to 1280x800

Unfortunately, it won't let me go abvoe 800x600. I went into the usr/.../applications/screens and graphics and select the resolution I wanted (I did try the Acer Aspire 56l to start with but it made everything off centre).

Now, I have tried to select 1280x800 but it put my settings to a black screen with LOTS of white dots all over it... Now I can not read anything being displayed and it seems to have damaged it.

Any ideas how I can sort this out?

Thanks

---

### Post by Patb on 2008-05-20
Amnesia, first back up your present settings.  In a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
```
Then try reconfigure your X settings
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If that doesn't give you a workable screen resolution, try it without the -phigh option (then includes low priority questions):
```
sudo dpkg-reconfigure xserver-xorg
```
Please post whether this gets you anywhere.  

Cheers, Pat.

---

### Post by Amnesia180 on 2008-05-20
Hi,

Thanks for your help, I have managed to run it in recovery mode, then typed in "init2" which brought my back up and running.

For some reason, it just won't let me select 1280x800!

---

