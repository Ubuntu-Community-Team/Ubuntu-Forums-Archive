---
title: "need help with nvidia 5200 video card..."
date: 2008-05-12
forum: General Help
---

### Post by Mia_tech on 2008-05-12
I've installed a new nvidia 5200 video card in my ubuntu box, but it won't boot to the x session, it will only boot in recovery mode, I've tried changing the driver section in the xorg.conf file to nvidia, with no luck...could someone give me a hand getting this to work?...here's a copy of my xorg.conf file
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

thanks

---

