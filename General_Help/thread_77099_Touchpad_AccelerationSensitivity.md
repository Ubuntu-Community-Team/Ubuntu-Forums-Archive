---
title: "Touchpad Acceleration/Sensitivity"
date: 2005-10-16
forum: General Help
---

### Post by Assneck on 2005-10-16
Just put 5.10 on a Dell laptop and the touchpad settings don't seem to be working.  I'm trying to use the Mouse settings to adjust the touchpad accleration/sensitivity and its turned all the way down with no effect to the touchpad speed.  The touchpad works very well, touch clicking works, cursor works, only problem is it moves way to fast.  I'm guessing the Mouse settings are changing settings to the PS/2 which isn't connected, but may be used in the future.  Is there a way to adjust touchpad sensitivity independent of the PS/2 mouse?

---

### Post by pbearsailor on 2005-10-16
[http://ubuntuforums.org/showthread.php?t=75094&page=2]("http://ubuntuforums.org/showthread.php?t=75094&page=2")  :smile:

---

### Post by strips on 2005-10-16
I have a Dell Inspiron 8600 with Alps touchpad. I follow what this page to get most out of a Synaptic / Alps touchpad:
[http://web.telia.com/~u89404340/touchpad/]("http://web.telia.com/~u89404340/touchpad/")

To change the sensitivity you need to modify MinSpeed, MaxSpeed and/or AccelFactor in the synaptics section in xorg.conf.

All you need is the xorg synaptics driver wich installs default and the correct section in xorg.conf.

Here is my **tweaked** InputDevice section:
```
Section "InputDevice"
	Option		"CorePointer"
	Driver		"synaptics"
	Identifier	"Alps Touchpad"
	Option		"Device"  		"/dev/input/event2"
	Option		"Protocol"		"event"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"970"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"700"
	Option		"FingerLow"		"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"20"
	Option		"HorizScrollDelta"	"20"
	Option		"MinSpeed"		"0.4"
	Option		"MaxSpeed"		"1.1"
	Option		"AccelFactor"		"0.015"
	Option		"EdgeMotionMinSpeed"	"15"
	Option		"EdgeMotionMaxSpeed"	"15"
	Option		"UpDownScrolling"	"1"
	Option		"CircularScrolling"	"1"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"2"
	Option          "SHMConfig"             "on"
	Option          "Emulate3Buttons"       "true"
EndSection
```

WARNING: Theese settings are for Alps touchpad and they are tweaked to my preferance. For the default Alps and Synaptics settings see **/usr/share/doc/xorg-driver-synaptics/README.Debian** and **/usr/share/doc/xorg-driver-synaptics/README.alps**.

---

### Post by Assneck on 2005-10-17
thanks...i swear i used the search function and didnt find anything! lol:D

---

