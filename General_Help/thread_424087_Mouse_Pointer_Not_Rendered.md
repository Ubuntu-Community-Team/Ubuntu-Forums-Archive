---
title: "Mouse Pointer Not Rendered"
date: 2007-04-26
forum: General Help
---

### Post by Derspankster on 2007-04-26
I recently upgraded to Feisty from Edgy. I run a EVGA Nvidia 6200 video card. After upgrading, my video card didn't work. I installed everything pertaining to Nvidia and then installed the following;

linux restricted modules 2.6.20.5-15-20
nvidia -glx-new
nvidia-glx-dev
nvidia-kernel-common 
nviidia-new-kernel-source
restricted-manager
xserver-xorg-video-nv

So - I should be running th 9755 nvidia driver for the geforce 6200. Everything works fine except that my mouse pointer is not rendered and appears as a fuzzy square and not an arrow. It functions as a pointer if positioned correctly. It's just not rendered.  Beryl runs OK, it's just this mouse issue. Below is my xorg. I've been searching for a solution for several days now and haven't run into anyone that has had a similar issue.
Here's my xorg.


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Nvidia Geforce 6200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Acer AL1917"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia Geforce 6200"
	Monitor		"Acer AL1917"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"


	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by kubusz on 2007-04-29
Hi,

I have upggraded to from Edgy Efy to Feisty Fawn and I am having troubles with running 2 monitors. On my primary monitor (notebook) the mouse cursor is ok, but when I go on the second monitor (19" widescreen) the mouse cursor turns into a wierd square and I am not able to force it to be normal cursor ...?

I had the same problem in Edgy Eft, but I solved by puting these lines in xorg.conf:

Section "Extensions"
  Option "Composite" "disable"
EndSection

but when I tried this in Feisty Fawn the X server didn't run at all and I had to remove it.

Do you have any ideas how to solve the square mouse cursor?

Thanks Kubusz

---

