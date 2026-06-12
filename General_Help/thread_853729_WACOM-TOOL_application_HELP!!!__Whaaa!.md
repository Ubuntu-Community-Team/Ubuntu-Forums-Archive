---
title: "WACOM-TOOL application HELP!!!  Whaaa!"
date: 2008-07-08
forum: General Help
---

### Post by sirbingo on 2008-07-08
HELP!!  How do I get my Wacom tablet to work in UBUNTU.

It kinda works right off the bat...but I installed the WACOM-TOOL application that supposedly lets you configure the tablet.  

Well now that its installed how do I launch this configuring utility?  Am I making any sense here?!?  

Ugh!  I am such a noob!](*,)

---

### Post by Car60n on 2008-07-08
I guess you could start it by typing wacom-tools in the terminal

---

### Post by fragos on 2008-07-09
All that's required is to edit /etc/X11/xorg.conf. Here's what was required for my USB connected Wacom Graphire4.

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"USB"           "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"        "/dev/input/wacom"
	Option		"Type"          "pad"
	Option		"USB"           "on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
EndSection

---

