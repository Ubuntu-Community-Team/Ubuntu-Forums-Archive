---
title: "Change color depth"
date: 2007-04-30
forum: General Help
---

### Post by funnyguyfunnyguy on 2007-04-30
How do I change the color depth on Ubuntu from 24/32 bit to 16 bit? I think that I can edit xorg.conf to change this, but is there a simpler way?

---

### Post by marleyfan68 on 2007-04-30
It is fairly easy to edit /etc/X11/xorg.conf and make the change quickly:

[code] sudo gedit /etc/X11/xorg.conf

Find the Section "Screen" (near the end of the file), looks like this:

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation GeForce Go 7900 GS"
	Monitor		"Generic Monitor"
	Defaultdepth	24

Change the default depth entry to 16

Thats all there is too it!

Quick and easy!

marleyfan68

---

