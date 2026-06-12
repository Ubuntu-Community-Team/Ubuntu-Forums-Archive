---
title: "ATI Display Drivers &amp; Incorrect Resoultion"
date: 2008-02-20
forum: General Help
---

### Post by SyrusTV on 2008-02-20
Hi there;

Finally got around to fixing my grub to actually boot my Ubuntu 7.10 install after I stupidly tried Vista and messed up my boot manager and well things didn't go according to plan...
I used fiesty fawn; but never bothered doing anything other than programming in it so left default resolutions etc and it never became my primary OS due having an xfi card and hence no sound. Now I use it at uni everyday I want to commit and get it fully working on my home machine.

But...

No matter what I seem to try and do I cannot get my display drivers to work and display at a resolution greater than 800x600.

xorg.conf
```

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
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1680"	"1680x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
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
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```


Restricted ATI driver confirmed enabled.

My control center doesnt open at all.

aticonfig -initial just gives me 
```
-ubuntu:~$ aticonfig -initial
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

```
But as i've copied the above conf file ^^ it obv does exisit.

But I know I've got a problem as;

```

-ubuntu:~$ sudo fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

```

So meh; any advice?
Am I being a tard?

Anything else you need before I go blind staring at pixels the size of my fist? :D

---

### Post by ahmed_zaghloul on 2008-02-21
thanx for ur efforts

---

