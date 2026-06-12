---
title: "Drag and drop across monitors"
date: 2008-02-29
forum: General Help
---

### Post by theadmiral on 2008-02-29
I can't drag and drop open windows from one monitor to another. Anyone know of a workaround for this.
Similarily I cant open firefox on both monitors at the same time.
i cant imagine i am the only one who would like to see this changed

---

### Post by rapiscan on 2008-02-29
The solution is to have a single desktop stretched accross your monitors, but we need a little more information to help you out.

What is the make/model of your video card?

---

### Post by theadmiral on 2008-03-05
ati radeon 9550

Also here is the important part of my xorg.conf



Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" LeftOf "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "AH191"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection


Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor    "AH191"
	DefaultDepth     24
	SubSection "Display"
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

---

### Post by rapiscan on 2008-03-06
Try using the ATI Big Desktop method for dual monitors:
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

---

