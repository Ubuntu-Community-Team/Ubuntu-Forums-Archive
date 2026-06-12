---
title: "Xorg config not working"
date: 2008-03-19
forum: General Help
---

### Post by Honken on 2008-03-19
Heya

I've been trying to enable dual-head with my Xorg config, without luck. When I boot it tells me that Xubuntu is running in low-graphics mode (or something similar, forgot to write it down). 

Here's my Xorg config:

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"1950XT0"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"1950XT1"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Samsung Syncmaster 730BF"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"DELL M992"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"1950XT0"
	Monitor		"Samsung Syncmaster 730BF"
	Defaultdepth	24
	SubSection "Display"
		HorizSync 	30-81
		VertRefresh 	75
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"1950XT1"
	Monitor		"DELL M992"
	Defaultdepth	24
	SubSection "Display"
		HorizSync 	30-96
		VertRefresh 	85
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Multihead"
  	Screen "Screen0"
	Screen "Screen1" RightOf "Screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Option "Xinerama"
EndSection

Section "ServerFlags"
Option "xinerama" "true"
Option "DefaultServerLayout" "Multihead"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection


I'm using a 1950XT with the official FGLRX drivers.

Any ideas? I'm kinda stuck here.

Thanks!

---

