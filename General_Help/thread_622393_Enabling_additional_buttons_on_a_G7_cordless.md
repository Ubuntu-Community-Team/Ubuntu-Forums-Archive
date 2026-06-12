---
title: "Enabling additional buttons on a G7 cordless"
date: 2007-11-24
forum: General Help
---

### Post by iarp on 2007-11-24
Hey,

I've been trying to get my mouse's additional buttons to work, in particular the side button for going Back on web pages and wheel click-in for 4 way scrolling.

I've tried doing everything listed here. [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto) but i'm unable to save it.

I keep getting told: 
Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

Just to verify i'm going from:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

TO

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"6 7"
	Option		"Buttons"	"7"
	Option		"Emulate3Buttons"	"false"
	Option     	"ButtonMapping" "1 2 3 4 5 6 7"
EndSection

EDIT: Just an FYI, this is the second day i've been on Ubuntu, so it maybe some simple but i'm still getting used to a few things.

---

