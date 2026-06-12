---
title: "Fullscreen Games Don't Work With Monitor"
date: 2008-03-17
forum: General Help
---

### Post by liam848 on 2008-03-17
I'm wondering if anyone can help me with a really annoying problem I have. Every time I try to run a game that displays in fullscreen, like Frets on Fire, my monitor just displays a message which says "NOT SUPPORT; RECOMMEND 1280 x 1024 60HZ". No matter what I try I just keep getting this blank screen with the message from the monitor. I'm running 7.10 and have an Ati Radeon 9550, which has drivers installed for it through Envy.

---

### Post by danwood76 on 2008-03-17
It might be that the games are setting a refresh rate too high for you graphics card or monitor. (probably the monitor)

Also your monitor may not be correctly setup in your xorg.conf.
You could try running the ati initial config app to check the driver loads properly:
```

sudo aticonfig --initial

```

---

### Post by liam848 on 2008-03-17
Thanks for your quick reply. When I run aticonfig --initial I just get

```
Found fglrx primary device section
Nothing to do, terminating.
```

The problem is most likely the way the monitor is set up in the xorg.conf but I dont really know enought to mess about with it.

---

### Post by forrestcupp on 2008-03-17
backup xorg.conf and post the contents of this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo gedit /etc/X11/xorg.conf
```
But if you use sudo, don't change anything until you know what you're doing.

---

### Post by liam848 on 2008-03-17
Here's the contents of my xorg.conf:

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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

Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	InputDevice     "Wiimote" "AlwaysCore"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Everything was generated automatically, with the exception of the settings for the wiimote, which were done long after I first noticed this problem.

---

### Post by danwood76 on 2008-03-17
Try running
```

sudo dpkg-reconfigure xserver-xorg

```

This is a wizard that will helpo you setup your vid card.
You can set the available modes for your monitor which might help.
Choose fglrx as the driver btw.

---

