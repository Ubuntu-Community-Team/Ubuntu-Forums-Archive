---
title: "Refresh rate 50Hz w/ 22'' Samsung LCD"
date: 2008-01-02
forum: General Help
---

### Post by sethfc on 2008-01-02
Hey all, just reinstalled Ubuntu 7.10 64bit, and I got a new Samsung 226BW 22'' LCD monitor =o

When I goto System > Preferences > Screen Resolution, it says i'm runing 1680x1050 @ 50 Hz.  Naturally, an LCD should run 60 Hz, and that's better for my eyes.

I've read threads to where this is a "bug", but i'm not entirely sure.

This is my xorg:

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
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
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

```

any advice?

thanks,
seth

P.S.: GFX Card: 7800GT 256MB PCI-E

---

### Post by Jerry N on 2008-01-02
I get the same thing with my Samsung 940t with Ubuntu, LinuxMint 4, and some other Linux distributions that I have tried.  However, when I check the monitor itself it claims that it is working at a refresh rate of 60.  I have decided to quit worrying about it.

Jerry

---

### Post by perlluver on 2008-01-02
You can also try installing the restricted drivers for your video card, and it says it is a Generic Monitor.  Hopefully that will help a little more.

---

### Post by sethfc on 2008-01-02
In the top right corner of my desktop, there is an icon that says I am using the nvidia restrictive driver.  I am also using 'normal' desktop effects, so i can use compiz (so i'm pretty sure the driver is in use o_0

---

### Post by perlluver on 2008-01-02
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection



This part of your xorg, go to System>Administration>Screens and Graphics, andtry tofind your monitor in the list.  Also check the screen refresh on your monitor itself, it might already be at 60.

---

### Post by melopsittacus on 2008-01-02
Hi, I am also using the nVidia restricted driver (NVIDIA accelerated graphics driver -- latest cards) with an LCD monitor (ViewSonic) and I was able to fix the refresh rate with nVidia's own settings program. 
To access it you have to type```
nvidia-settings
``` in a terminal. Then in the settings window go to X Server Display Configuration and set the refresh rate. 
For me, Gnome's built in screen resolution tool still displays the wrong refresh rate (50Hz) but in the monitor's settings window reports it as 75Hz.

---

### Post by perlluver on 2008-01-02
> **melopsittacus said:**
> Hi, I am also using the nVidia restricted driver (NVIDIA accelerated graphics driver -- latest cards) with an LCD monitor (ViewSonic) and I was able to fix the refresh rate with nVidia's own settings program. 
To access it you have to type```
nvidia-settings
``` in a terminal. Then in the settings window go to X Server Display Configuration and set the refresh rate. 
For me, Gnome's built in screen resolution tool still displays the wrong refresh rate (50Hz) but in the monitor's settings window reports it as 75Hz.

Run sudo nvidia-settings, otherwise I don't think it will save.

---

