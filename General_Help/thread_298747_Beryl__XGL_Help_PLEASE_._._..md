---
title: "Beryl / XGL Help PLEASE . . ."
date: 2006-11-13
forum: General Help
---

### Post by davebed on 2006-11-13
I'm having some trouble with Beryl/XGl and would really appreciate some help. I've got Beryl running now on my Radeon x1400 (Inspiron e1505) and it looks great. My two main issues are:

_Issue #1_
In XGL/Beryl I cannot get my DPMS to work - I want my laptop screen to a)Blank on close b) blank after 10min on AC and c)blank on 2 min on battery. I've seen some posts on a workaround by using ```
DISPLAY=:0 xset dpms X
``` where X = seconds before off, ([http://ubuntuforums.org/showthread.php?t=282229&highlight=dpms](http://ubuntuforums.org/showthread.php?t=282229&highlight=dpms)) but I can't figure out how to implement that into my situation (or if it's the best solution for me...)

Running **xset q** gives:```
DPMS (Energy Star):
  Display is not capable of DPMS

```

Further, I find that the settings made in **gconf-editor** to power management stuff don't seem to take hold either... Is there any way to get all my power managment things to work with XGL/Beryl?

_Issue #2_
When loading XGL the Beryl "Select Window Manger" *always* defaults to Compiz (i never got *that* working and thought I had removed it) instead of Beryl. I have to manually change it every time](*,) .



BTW, **fglrxinfo** gives:
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6065 (8.29.6)

```
Thanks for any help you can offer. The relevant section of my Xorg.conf is beleow (are there dual entries for Device and Monitor? or is it supposed to be like that?)
```
Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by organica on 2006-11-13
I have not spent much time with ATI drivers, but the dual entry for the ATI card is a little strange.  It seems your ATI card has a dual monitor capability?  If so, try stiching the "vesa" driver to "fglrx"  give it a reboot and see how it goes.  Sorry can't give any more info.  Just go back to a HOWTO for ATI/Beryl/XGL and read it word-for-word.

---

### Post by strabes on 2006-11-13
try in the xgl irc channel #ubuntu-xgl on freenode

---

