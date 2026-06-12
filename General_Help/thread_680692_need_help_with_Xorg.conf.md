---
title: "need help with Xorg.conf"
date: 2008-01-28
forum: General Help
---

### Post by xs123 on 2008-01-28
I have SLI

When using windows / anything else, i have my monitor connected to the First Video card, except with ubuntu I get no picture unless i connect it to the Second Video card

So, I am asking, in Xorg.conf i have

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	Busid		"PCI:4:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"

Will changing the Busid to PCI:3:0:0 fix this? or screw up everything?

---

### Post by Jimmey on 2008-01-28
It depends upon which of the PCI bus IDs your second graphics card is on.

If you're sure that it's PCI:3:0:0, then there's no problem. I think that you can check by running ```
lspci | grep nVidia 
``` in a terminal window (note that this is case sensitive. if this command fails, just run ```
lspci
``` normally).

The best way of sorting your xorg out is to exectue ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
``` to create a backup, before you do anything.

Then, if the sh*t hits the fan, you can re-instate this backup by typing ```
cp /etc/X11/xorg.conf.BACKUP /etc/X11/xorg.conf
```

Then try.

---

