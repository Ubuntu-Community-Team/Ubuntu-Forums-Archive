---
title: "Kubutu can't find my 2nd screen"
date: 2008-03-17
forum: General Help
---

### Post by lalimannen on 2008-03-17
My problem is that Kubuntu 7.10 can't seem to find my second screen. I wanna have dual screen. I use the x86-version on my x64-machine. The graphic card is a 6200 with one DIV and one VGA output.

I have used different ways to install the drivers; envy and *restricted drivers* in *system settings*. I now use the envy - drivers.

The Nvidia-settings only show me one of the screens.

When I boot up both screens is showing a clone, but when the login screen appears the DVI-screen hibarnates and the VGA-screen is left alone.

I search the forum and the internet and all I can find is that i should modify xorg.conf - and so I've done - so many times! With various results! =P 

So, please please, someone who knows what she/he is doing - help!

(And forgive me for my english, it's not my mother tongue)

---

### Post by lalimannen on 2008-03-20
Heres my xorg.conf as it is today. 
When I run it it says that my Monitor 0 is undefined.
I don't know what to change?
Please help me.

```
Section "Device"
Identifier "6200 0"
Driver "nvidia"
Option "NoLogo" "true"
Option "RenderAccel" "true"
Screen 0
BusID "PCI:2:0:0"
EndSection

Section "Device"
Identifier "6200 1"
Driver "nvidia"
Option "NoLogo" "true"
Option "RenderAccel" "true"
Screen 1
BusID "PCI:2:0:0"
EndSection

Section "Screen"
Identifier "Screen 0"
Device "6200 0"
Monitor "Monitor 0"
DefaultDepth 24
Option "ConnectedMonitor" "CRT-0"
Subsection "Display"
Depth 24
Modes "1400x900" "1280x1024"
EndSubsection
EndSection

Section "Screen"
Identifier "Screen 1"
Device "6200 1"
Monitor "Monitor 1"
DefaultDepth 24
Option "ConnectedMonitor" "DFP-0"
Subsection "Display"
Depth 24
Modes "1680x1050" "1280x1024"
EndSubsection
EndSection



Section "ServerLayout"
	Identifier	"Default Layout"
Screen 0 "Screen 0"
Screen 1 "Screen 1" LeftOf "Screen 0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

