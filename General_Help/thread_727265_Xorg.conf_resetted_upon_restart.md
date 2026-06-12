---
title: "Xorg.conf resetted upon restart"
date: 2008-03-17
forum: General Help
---

### Post by Firehalk on 2008-03-17
There are similar topics but I didn't see solution on those :(

I'm trying Ubuntu 8.04 alpha, but this problem was found already on 7.10.

When I restart my PC, my xorg.conf file is resetted to the default configuration (so my resolution goes to 640x480 and all that). Lucky, I always make a backup of it, but on all reboots fix it is pretty boring...

My question is: is there a way to do not let Linux reset xorg.conf?

My xorg.conf is pretty simple:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"OpenChrome"
	Busid		"PCI:1:0:0"
	Driver		"openchrome"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

I know there it says 640x480... but somehow this xorg.conf works for me to change resolution, while the other one (the default values) don't.

VGA: Via UnChrome PRO IGP
Monitor: Samsung Syncmaster 796mb Plus (it's listed there on drivers, but doesn't work :()

Thanks for any help.

---

