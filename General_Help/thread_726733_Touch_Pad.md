---
title: "Touch Pad"
date: 2008-03-17
forum: General Help
---

### Post by badspell68 on 2008-03-17
Does anyone know of a touch pad, easily installable app or driver for Ubuntu newest distro that provides me all the functionality on a Dell laptop d610. The one in the distro does not totally work i have to lift and move my finger several times to go across the screen?????

---

### Post by PurposeOfReason on 2008-03-17
> **badspell68 said:**
> Does anyone know of a touch pad, easily installable app or driver for Ubuntu newest distro that provides me all the functionality on a Dell laptop d610. The one in the distro does not totally work i have to lift and move my finger several times to go across the screen?????
What are you trying to do? The xorg.conf file can adjust a lot like speed.

---

### Post by badspell68 on 2008-03-17
Just trying to move around the screen easily, seems like the mapping is way off and I can't figure it out. I have to lift my finger from the pad and replace it several times to move anywhere on the screen. I can’t simply make a quick move across the screen.

---

### Post by PurposeOfReason on 2008-03-17
For an example, here is the toucpad part of my /etc/X11/xorg.conf. Don't copy past it as the identifier and others are probably different.
```
Section "InputDevice"
    Identifier "TouchPad"
    Driver "synaptics"
    Option "SendCoreEvents"
    Option "Protocol" "auto-dev"
Option "LeftEdge" "60"
Option "RightEdge" "930"
Option "TopEdge" "115"
Option "BottomEdge" "710"
Option "FingerLow" "14"
Option "FingerHigh" "15"
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "RTCornerButton" "2"
Option "RBCornerButton" "3"
Option "TapButton2" "2"
Option "SHMConfig" "true"
EndSection
```

It's pretty obvious what is all does but if not, type "man synaptics" in a terminal. Use the command
```

synclient -m 100
``` to find the x and y values of your touchpad. Just move around on it while it is running.

---

### Post by badspell68 on 2008-03-17
The identifier list as the same on mine...would a cut and past work?

---

### Post by PurposeOfReason on 2008-03-17
> **badspell68 said:**
> The identifier list as the same on mine...would a cut and past work?
It would "work" but my dimensions are probably different than yours as how fast I like my mouse etc.

---

### Post by badspell68 on 2008-03-17
synclient -m 100 Gave me this:

jeff@jefflaptopdell:~$ synclient -m 100
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0

And nothing changed. Can't seem to change anything I used the GUI to try and calibrate but it would not go past the adjust touch pad borders stage.
?

---

### Post by PurposeOfReason on 2008-03-17
> **badspell68 said:**
> synclient -m 100 Gave me this:

jeff@jefflaptopdell:~$ synclient -m 100
    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0

And nothing changed. Can't seem to change anything I used the GUI to try and calibrate but it would not go past the adjust touch pad borders stage.
?
That what it'll give you have first because you're not using the touchpad. Type in that command and start moving on the pad with that running and the numbers will change.

---

### Post by badspell68 on 2008-03-17
Did not change at all even when using the pad for an extended time period.

---

### Post by PurposeOfReason on 2008-03-17
> **badspell68 said:**
> Did not change at all even when using the pad for an extended time period.
I mean the numbers. Run the command and while it is running, trace the outline of your pad. Then post everything it says.

---

### Post by badspell68 on 2008-03-17
Yes, tried that. Numbers sis not change/

?

---

### Post by PurposeOfReason on 2008-03-17
> **badspell68 said:**
> Yes, tried that. Numbers sis not change/

?
First, do 
```
sudo aptitude install synaptics
```
to make sure you have the driver.

Well the best I can give you is copy past my dimensions and guess check with this
synclient LeftEdge=60
synclient RightEdge=930
synclient TopEdge=115
synclient BottomEdge=710

Run those at in a terminal, one at a time guessing each time where you want it. It won't stay changed though, you'll edit the xorg.conf file when you have the value you want. You can do that for any of the variables listed in my xorg.conf.

---

### Post by badspell68 on 2008-03-17
Must be a bigger problem going on as nothing changed.

---

### Post by PurposeOfReason on 2008-03-17
Can you post your xorg.conf?

---

### Post by badspell68 on 2008-03-17
Here it is:



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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "on"
EndSection


Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Inputdevice     "Synaptics Touchpad"


# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by PurposeOfReason on 2008-03-18
Try this:
```
Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "60"
Option "RightEdge" "930"
Option "TopEdge" "115"
Option "BottomEdge" "710"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "SHMConfig" "on"
EndSection


Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies Inc M22 [Mobility Radeon X300]"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc M22 [Mobility Radeon X300]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "1400x1050"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
Inputdevice "Synaptics Touchpad"


# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection 
```

If it moves faster after restarting X, we're good. You'll have to play with the dimensions though.

---

### Post by badspell68 on 2008-03-20
WOW!!!

Much better, but it still does not track the whole screen with one swipe across the pad. Goes off the screen a bit on the right side too...what setting is the right side?


THANKS!

---

### Post by PurposeOfReason on 2008-03-20
> **badspell68 said:**
> WOW!!!

Much better, but it still does not track the whole screen with one swipe across the pad. Goes off the screen a bit on the right side too...what setting is the right side?


THANKS!

The right edge. If you think  it needs to be bigger, make the number bigger etc. Do that for all of them. I don't know your dimensions, those are mine.

---

### Post by badspell68 on 2008-03-20
Thanks so much for the help!

---

