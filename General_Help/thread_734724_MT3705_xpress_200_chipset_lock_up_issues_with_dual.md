---
title: "MT3705 xpress 200 chipset lock up issues with dual screens"
date: 2008-03-25
forum: General Help
---

### Post by brw02005 on 2008-03-25
well after alot of work I have come up with two ways of dual screening with a big desktop for a MT3705 with an xpress 200 chipset.  The first involves using the open source ati driver and the second uses fglrx.  My girlfriend likes the pretty compiz eyecandy with the fglrx version but the problem is that it ocassionally locks up. Just wondering if anyone had any clues.  I found doing a single fglrx screen easy and stable but the problem only happens when I double up.  I will leave the two different versions here for anyone else trying to get this working with gutsy.

With the open source ati driver
I use the conf below to create a dual clone and then with the command

sudo xrandr --output VGA-0 --left-of LVDS

to make it big desktop dual screen with the external screen to the left

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"0 ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"ati"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Labtop Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Labtop Screen"
	Device		"0 ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Labtop Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	Virtual 2560 800
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
        screen 0 "Labtop Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

I used envy to install the latest fglrx drivers
after using the conf below I go into the catalyst control center enable the second screen (if yours is not working) which cause it to fritz out (you'll see what I mean if you have to do it) then saved it and restarted.  The second time it should load up in clone mode and then you just have to select big desktop from the catalyst control center you will need to repeat this step every time you reboot.  I couldn't get compiz to work at larger resolution but it could be because of the windows 98 CRT I'm using. keep in mind this does work but will lock up ocassionally.


Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option	    "DesktopSetup" "horizontal,reverse"
	BusID       "PCI:1:5:0"
	Screen      0
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Modes "1024x768"
		Depth     24
	EndSubSection
EndSection

The following was working in gutsy with the exception of occasional lockups with fglrx version what I am looking for is possible fixes for the lockup as well as alterations to the conf to enable dual screen big desktop at boot up.  I don't want instructions for dual screen xinerama either.

---

