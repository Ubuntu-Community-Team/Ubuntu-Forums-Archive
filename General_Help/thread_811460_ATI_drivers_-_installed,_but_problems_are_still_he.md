---
title: "ATI drivers - installed, but problems are still here"
date: 2008-05-29
forum: General Help
---

### Post by primky on 2008-05-29
Well, I'm using Ubuntu with Hardy. I installed driver with step-by-step tutorial.
This is what i've  done:

**1.)** sudo apt-get install linux-restricted-modules-2.6.24-17-generic xorg-driver-fglrx fglrx-control  (my kernel is 2.6.24-17-generic)
**2.)** sudo gedit /etc/X11/xorg.conf (added some lines, i'll show you xorg.conf later)
**3.)** reboot
**4.)** fglrxinfo (it says it's Mesa, not ATI)


This is my xorg.conf file:

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
Load "GLcore"
Load "glx"
Load "dri"
Load "extmod"
SubSection "extmod"
Option "omit xfree86-dga" 
EndSubSection
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "si"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "UseInternalAGPGART" "no" 
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

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection



Please help me!! What's wrong?

---

### Post by primky on 2008-05-29
Why nobody helps me?

---

### Post by pointone on 2008-05-29
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers)

---

