---
title: "Multiple issues in Feisty"
date: 2007-10-03
forum: General Help
---

### Post by Jive Turkey on 2007-10-03
I'm hoping someone can point me to a solution for some of these issues, or at least help me figure out where  I can poke around to resolve the problem.

Hardware:
AMD Athlon 2600+
1GB ram
ATI 9800 Pro flgrx driver - dualhead/big desktop
creative audigy 2 platinum sound card
MS multimedia keyboard

1)the binary flgrx driver has very weak processing power, 3D rendering is a joke compared with the open driver, I suspect that the CPU is doing all of the work.   however, I couldn't get Dual monitors to work except in clone mode using the open driver. so I would like to either get Dual monitors for the open driver, or better 3D with the binary driver.  The guides at community docs don't seem to work for me on enabling dual mon with the open driver:confused: I spent about 10 hours trying with no joy.

2)My keyboard volume control is mapped correctly according to "Keyboard Shortcuts" under System>Preferences>Keyboard Shortcuts.  When I press the volume up and down keys the OSD comes up in the middle of my primary monitor, and the level meter responds to the key strokes. However the volume does not change, it isn't linked to the system volume for some reason.

3)I'm using a dark theme "Divinorum" from gnome-look.  certain web pages and applications will occasionally have white text on white background, or black on black.  The theme "does not support color schemes" under the  theme details dialogue, so I would like some tips on tweaking the theme's source to change the text colors from white to lite grey or blue, and black to dark grey or dark blue so that it is more visible.

Thanks in advance for any suggestions.

---

### Post by peabody on 2007-10-03
I'm surprised the fglrx driver wouldn't do 3D well.

What does

glxinfo | grep direct

give you in a terminal running under the fglrx driver?

---

### Post by Jive Turkey on 2007-10-04
> **peabody said:**
> I'm surprised the fglrx driver wouldn't do 3D well.

What does

glxinfo | grep direct

give you in a terminal running under the fglrx driver?

Thanks for the reply,
:~$ glxinfo | grep direct
direct rendering: Yes

Here is the relevant part of my xorg.conf:
```
Section "Monitor"
	Identifier   "Monitor0"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Radeon 9800"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "DesktopSetup" "horizontal"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "OverlayOnCRTC2" "0"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "ATI Radeon 9800"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "ATI Radeon 9800"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

I reverted back to the open driver temporarily, I ran "armagetron" at 90-300 fps, with some artifact visible, with the fglrx driver I got 2-30 fps.  Also, none of the desktop effects ie: wobbly windows etc work with the restricted driver.  Also tuxkart is barely playable with either driver, as in not rendered correctly and <2 fps.

---

