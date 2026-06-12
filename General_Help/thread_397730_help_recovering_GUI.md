---
title: "help recovering GUI"
date: 2007-03-31
forum: General Help
---

### Post by cptjaben on 2007-03-31
I just bought an [Asus f3jp]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220141") laptop. it came preinstalled with vista, i resized the hdd and made another partion and installed ubuntu 6.06. I then upgraded to edgy using [this guide]("http://ubuntuforums.org/showthread.php?t=227052"). When I boot up edgy, everything appears to be going fine until the login screen at which point the the graphical interfaced gets complety messed up. everything else seems to be working, i.e. i can log in and use other parts of the desktop, it would be like if you had your monitor turned off. Is there a way that i can reset my video drivers or something of the sort?

Thanks

---

### Post by zvacet on 2007-03-31
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cptjaben on 2007-03-31
is there a keyboard shortcut that would let me open a terminal? I changed the default setting on my desktop a long while ago and have since forgot the default.

Thanks

---

### Post by taurus on 2007-03-31
<Alt>F2 -> gnome-terminal or <Ctrl><Alt>F2 to get to a console.

---

### Post by cptjaben on 2007-03-31
awesome, i'll see if that works.

Thanks

---

### Post by cptjaben on 2007-03-31
Is there a way I can install the fglrx drivers through the terminal or console? If so how would I got about doing it? Thanks

---

### Post by cptjaben on 2007-03-31
ahh nm, I figured it out.

---

