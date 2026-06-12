---
title: "Gnome won't load."
date: 2007-12-12
forum: General Help
---

### Post by mbf2k on 2007-12-12
I am running Ubuntu 7.10 on a Dell Lattitude D531, x86. My desktop effects would not start when I tried to turn it on, so being the genius that I am I decided to use a different device driver for my graphics card. When I changed my device driver to a manual one for a similar (but not the same) graphics card my display went black, and when I did a reboot Gnome wouldn't start. I have a command prompt and I can login, but I don't know how to reset my Gnome to default, etc... HELP!

---

### Post by iraiscoming223 on 2007-12-13
First of all: **You've created a backup copy of xorg.conf** (so you're ok! :P)
just type
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
and reboot

Second: **You don't have a copy of xorg.conf BUT you're able to use vi**
just type
```
sudo vi /etc/X11/xorg.conf
```
edit your file and save/quit
```
w!
q!
```

Third: **None of the choices above** :lolflag:
insert a live cd disc and boot it, (assuming you're using GNOME)
then open a terminal, type
```
su gedit /etc/X11/xorg.conf
``` 
and edit it.

In both the second and third case you (should) just have to edit the driver string... :)

byeee

---

### Post by danwood76 on 2007-12-13
Or you could just delete the xorg.conf (or rename to xorg.bak) and the xserver will use default drivers.

---

