---
title: "laptop and external: cloning display with different resolutions"
date: 2007-11-13
forum: General Help
---

### Post by phen on 2007-11-13
hello all!

maybe you can help me: since 2 years now I have the following problem:

at home, I use a docking station for my laptop with an external screen (high res). ideally, the laptop is closed, put on the station, powered on without opening or using the laptop display. at the university i want to use my laptop without an external display.

external display at home: 1280x1024
laptop internal display: 1024x786

it was never possible to realize this. maybe with the new xrandr, but I don't know how. Any hints? links to documents or threads? Before the new X, I had to open the lid, turn off the internal screen manually during boot when at home. At the moment, the screen is usable without configuration, even in the right resolution, but i am not able to maximize windows, because X thinks that the display uses the resolution of the internal display. please see my attached screenshot. the xorg.conf used is the standard one, with a single change I made (bold):

```

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		**"1280x1024"** "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice	"Synaptics Touchpad"
EndSection

```


I appreciate your help, thank y all!


kai

---

### Post by arpi_amsterdam on 2007-11-13
I have a similar problem and it seems to be related to compiz-fusion in my case anyway. Are you using visual effects ? 
So the issue is that the maximize button stretches my window up to the max of the laptop resolution (dell d620) which is smaller then the one I use with a docking station.
Probably we have to tell xorg in some way when to use the internal screen and when to use the external. Or maybe it is just compiz.. I dont know where to start debugging this

---

### Post by phen on 2007-11-14
I don't know either... I am thinking about trying a two display setup again. then I'd have to remove all acpi actions from the display-close event. should work...but stupid while using the laptop without docking station.

see the screenshot. i am using visual effects. but with older non output-hotplugable xorgs, I wasnt able to use the docking station comfortably. hope someone has an idea. how was it BEFORE compiz-fusion for you?

---

### Post by tact on 2007-12-03
I am using a Dell D410 laptop that has max 1024x768 resolution on the LCD and I connect it (via a "media base" docking station) to a Dell 19" external LCD monitor with max res 1280x1024

The new xorg seemed able to auto configure for each situation (internal LCD or external) but just as Gnome was starting the external LCD would flick from 1280x1024 into 1024x768.   After the desktop finished loading I would have to System>Admin>Screens and Graphics then change resolution manually back to 1280x1024

Then....  I found that if I change this key in gconf  /desktop/gnome/screen/default/0/resolution from 1024x768 to 1280x1024 things worked nicely.

When in the dock using the 19" external monitor gnome stays in 1280x1024.
When out of the dock and using the laptop LCD screen (despite the default set higher) gnome boots nicely as 1024x768

---

