---
title: "Tablet Hardware and Keyboard Questions"
date: 2008-05-02
forum: General Help
---

### Post by MosMusy on 2008-05-02
I have some questions that have gone unanswered:

1) What drivers are necessary to download in order for me to be able to use my tablet pen?

2) Can I make a new keyboard layout where I can insert special characters? I've been searching for an easy way of inserting special characters (in word you can just assign a short cut key). I've been using macros, but they are a real pain to set up. Any body have better advice?

Thanks for your help

---

### Post by fragos on 2008-05-03
What tablet do you have? If it's Wacom compatible you will only have to add some bits to /etc/X11/xorg.conf

---

### Post by MosMusy on 2008-05-04
> **fragos said:**
> What tablet do you have? If it's Wacom compatible you will only have to add some bits to /etc/X11/xorg.conf

It's a Fujitsu LifeBook T Series

---

### Post by fragos on 2008-05-05
Most tablets are compatible with the Wacom driver. Here is my 8.04 xorg.conf with the Wacom changes I made. My tablet is a Graphire4 that is USB connected. I've marked the lines I added for Wacom with "|" as the 1st character. Remove the "|" when you use those lines.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

|Section "InputDevice"
|	Driver		"wacom"
|	Identifier	"stylus"
|	Option		"Device"	"/dev/input/wacom"
|	Option		"Stylus2" 	"3"  # set button to right click
|	Option		"Type"		"stylus"
|	Option		"USB"           "on"
|EndSection

|Section "InputDevice"
|	Driver		"wacom"
|	Identifier	"eraser"
|	Option		"Device"	"/dev/input/wacom"
|	Option		"Type"		"eraser"
|	Option		"USB"           "on"
|EndSection

|Section "InputDevice"
|	Driver		"wacom"
|	Identifier	"cursor"
|	Option		"Device"	"/dev/input/wacom"
|	Option		"Type"		"cursor"
|	Option		"USB"           "on"
|EndSection

|Section "InputDevice"
|	Driver		"wacom"
|	Identifier	"pad"
|	Option		"Device"        "/dev/input/wacom"
|	Option		"Type"          "pad"
|	Option		"USB"           "on"
|EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
|	InputDevice     "stylus"	"SendCoreEvents"
|	InputDevice     "cursor"	"SendCoreEvents"
|	InputDevice     "eraser"	"SendCoreEvents"
|	InputDevice     "pad"
EndSection

Section "Module"
	Load		"glx"
EndSection

---

