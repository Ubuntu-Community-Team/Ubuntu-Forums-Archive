---
title: "[SOLVED] missing cursor"
date: 2007-11-30
forum: General Help
---

### Post by Clark76 on 2007-11-30
I recently did a complete reinstall of Gutsy.  Before the install I had a cursor.  I deleted all the partitions on my computer then reinstalled Ubuntu.  During the install I had a cursor.  Install finished and now my cursor is missing or better described as invisible since if I move the mouse around icons will highlight when I believe the "invisible" mouse is over them.  I am able to click on them though.  Any ideas or should I do another install?  

Thanks for any advice on this matter.

---

### Post by -grubby on 2007-11-30
I had a similar problem. In a minute I will post how I fixed it. Ok open a terminal and type:
```
gksudo gedit /etc/X11/xorg.conf
```

and edit the lines below highlighted in red. ONLY THE RED ONES

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"	[COLOR="Red"]"true"[/COLOR]
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51G [GeForce 6100]"
	Driver		"nv"
	BusID		"PCI:0:5:0"
	[COLOR="Red"]Option		"HWCursor"	"off"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"eView 17f3"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51G [GeForce 6100]"
	Monitor		"eView 17f3"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

---

### Post by Clark76 on 2007-11-30
Thank you nathangrubb.  That did the trick.  Problem solved

---

