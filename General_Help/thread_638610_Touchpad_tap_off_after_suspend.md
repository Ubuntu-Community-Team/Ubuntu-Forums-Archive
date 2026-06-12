---
title: "Touchpad tap off after suspend?"
date: 2007-12-12
forum: General Help
---

### Post by fred168 on 2007-12-12
Hi,

I need help getting the touchpad tap to stay off after suspend. As described in many other places here, one can switch off the tap by adding

	Option		"SHMConfig" "true"
	Option		"MaxTapTime"	"0"

to the touchpad inputdevice section of /etc/X11/xorg.conf. 

However the tap comes back on after suspend (you must believe me on this). Is there some way to turn it off so it stays off? (is there another xorg.conf being used?)

This is driving my wife insane (e.g. on openoffice to open a menu one must traverse various buttons that inevitably get unintentionally clicked on...)

For clarity: this is not an issue of turning off the touchpad whilst typing, but to switch off the tap whilst moving the pointer.

Also here is the relevant part of my xorg.conf:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig" "true"
	Option		"HorizScrollDelta"		"10"
	Option		"VertScrollDelta"		"10"
#	Option		"HorizTwoFingerScroll"	"true"
#	Option		"VertTwoFingerScroll"	"true"
	Option		"LockedDrags"			"false"
	Option		"EdgeMotionUseAlways"	"true"
	Option		"EdgeMotionMinSpeed"   	"10"
	Option		"EdgeMotionMaxSpeed"    "200"
	Option		"EmulateMidButtonTime"	"100"
	Option		"MinSpeed" 				"0.5"
 	Option		"MaxSpeed" 				"1.0"
 	Option		"AccelFactor" 			"0.1"
	Option		"MaxTapTime"	"0"
EndSection

---

