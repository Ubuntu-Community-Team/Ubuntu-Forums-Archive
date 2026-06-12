---
title: "Xorg CPU Spikes"
date: 2008-03-20
forum: General Help
---

### Post by Mikersoft on 2008-03-20
Hello, this is my first post here on the forums, as I have only been using for about a week (something to do over spring break). Anyway, when viewing my system processes with the top command in terminal (system monitor uses a lot of cpu for me), it seems that my xorg process takes up 50%+ cpu whenever something happens on my screen. 

I have compiz fusion, and I have a good number (read: almost all) of the flashy effects enabled, but I have a 2.2 ghz dual core processor and an nVidia 8600M GT w/ 256 MB VRAM, so I don't think it's due to hardware, as Vista runs fairly smooth.

Still, for some reason, when I minimize/maximize/move windows, go to my desktop, switch windows, or even scroll down an image-intensive webpage in Firefox, my lappy seems to freeze for a sec, as if it's skipping a frame or two. If I show my desktop (i have the show desktop plugin in compiz enabled), then xorg takes up 83% of CPU, with compiz.real taking up the other 17%.

So basically, xorg spikes in CPU usage whenever anything changes on screen. Also, it takes up 850+ megs of virtual memory. I used Envy to install my nVidia driver, and I have my xorg.conf below. I'm using Gutsy Gibbon 7.10.

> 
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
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"UseFBDev"	"true"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option "UseEvents" "on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-84
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1680x1050"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
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
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


I really want to adopt Ubuntu as my main OS (I'm triple booting w/ Ubuntu, XP, and Vista), but if it lags when so much as switch windows, that might be a bit frustrating. Any help would be appreciated.

---

### Post by Mikersoft on 2008-03-20
Bump? This is incredibly frustrating. I even turned off all visual effects, and i get similar spikes.

---

### Post by Mikersoft on 2008-03-21
Since my last post, I have tried installing xserver-xgl, which greatly improved my performance, but it also disabled the nvidia-settings command :(. Apparently, people were having crappy performance with xserver-xgl installed, so I'm curious as to why my performance is better with the package.

Also, I've noticed that I have terrible 2D performance, as my glxgears gets at least 10000+ fps, but when I minimize a window, I lag like crazy.

Please help! :cry:

---

