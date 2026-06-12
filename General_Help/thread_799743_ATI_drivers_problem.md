---
title: "ATI drivers problem"
date: 2008-05-19
forum: General Help
---

### Post by ericus on 2008-05-19
I've tried to install my ATi driver for a while now, and it's just not working out. Followed several guides, but nothing seems to help.

Some outputs:
```

ericus@ericus-desktop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2

Segmentation Fault
```

```
ericus@ericus-desktop:~$ glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

Xorg.conf:
> 
Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"radeon"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"sv"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

I have a ATI Radeon 9550 card, running Ubuntu Hardy Heron.
Tried with envyng, the officiall installer from ati.com and some other things. Please, help me out. Thanks in advance.

---

