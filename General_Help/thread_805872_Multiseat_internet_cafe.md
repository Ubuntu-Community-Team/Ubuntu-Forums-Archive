---
title: "Multiseat internet cafe"
date: 2008-05-24
forum: General Help
---

### Post by Keithamus on 2008-05-24
Hi all,

I just got a job in an internet cafe, and convinced the manager to switch 4 out of 7 of our PCs to a Multiseated Kubuntu box. Obviously Im the one who is setting it up, and I've hit a few problems.

1. I've finally managed to get 2 screens to work. Both monitors are identical, and as you can see from my xorg below, identical in config. The only problem is, the first one sticks at 640x480. The second one is full 1440x900. As the xorg states, I dont even have 640x480 in the modes setup!

2. I have plugged in 2 usb mice... have them both down on the different layouts - but both mice control both monitors at the same time, I can even log in and do tasks on one, with either mouse, and see the cursor on the second login fly around also.

3. I've set up 7 logins (syn01 to syn07) and none have passwords - but when I doubleclick them in the KDM face browser, it says login failed!

See my xorg here:
```

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"DontVTSwitch"
	Option		"HandleSpecialKeys" "Always"
EndSection

################# Seat 1 #################
Section "InputDevice"
	Identifier	"Keyboard.1"
	Driver		"kbd"
#	Option		"Phys"		"*/input2"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Mouse.1"
	Driver		"evdev"
	Option		"Phys"		"*/input1"
EndSection

Section "Device"
	Identifier	"VideoCard.1"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	BusID		"PCI:1:0:0"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Monitor.1"
	Option		"dpms"
EndSection

Section "Screen"
	Identifier	"Screen.1.0"
	Monitor		"Monitor.1"
	Device		"VideoCard.1"
#	Defaultdepth	24
	SubSection "Display"
#		Defaultdepth	24
		Modes	"1440x900" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Seat.1"
	Screen		"Screen.1.0"
	InputDevice	"Mouse.1" "CoreMouse"
	InputDevice	"Keyboard.1" "CoreKeyboard"
	Option		"IsolateDevice" "PCI:1:0:0"
EndSection
################# END OF: Seat 1 #################

################# Seat 2 #################
Section "InputDevice"
	Identifier	"Keyboard.2"
	Driver		"evdev"
	Option		"Phys"		"*/input3"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Mouse.2"
	Driver		"evdev"
	Option		"Phys"		"*/input4"
EndSection

Section "Device"
	Identifier	"VideoCard.2"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	BusID		"PCI:2:0:0"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Monitor.2"
	Option		"dpms"
EndSection

Section "Screen"
	Identifier	"Screen.2.0"
	Monitor		"Monitor.2"
	Device		"VideoCard.2"
#	Defaultdepth	24
	SubSection "Display"
#		Defaultdepth	24
		Modes	"1440x900" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Seat.2"
	Screen		"Screen.2.0"
	InputDevice	"Mouse.2" "CoreMouse"
	InputDevice	"Keyboard.2" "CoreKeyboard"
	Option		"IsolateDevice" "PCI:2:0:0"
EndSection
################# END OF: Seat 2 #################

```


The relevant part of my kdmrc:
```

[X-:0-Core]
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=syn01
ClientLogFile=.xsession-errors
ServerArgsLocal=-br -audit 0 -layout Seat.1 vt09

[X-:0-Greeter]
DefaultUser=syn01

[X-:1-Core]
ServerArgsLocal=-br -audit 0 -layout Seat.2 -sharevts #-novtswitch vt09
[X-:1-Greeter]
DefaultUser=syn02

```

---

### Post by Keithamus on 2008-05-28
bump!

---

### Post by Keithamus on 2008-06-02
bump

---

### Post by aeiah on 2008-06-02
have you had a look at this?
[http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html](http://netpatia.blogspot.com/2006/09/multiseat-computer-with-ubuntu.html)

and in particular, this part of it:

[http://netpatia.blogspot.com/2006/09/multiseat-iv-evdev-and-xephyr.html](http://netpatia.blogspot.com/2006/09/multiseat-iv-evdev-and-xephyr.html)

---

