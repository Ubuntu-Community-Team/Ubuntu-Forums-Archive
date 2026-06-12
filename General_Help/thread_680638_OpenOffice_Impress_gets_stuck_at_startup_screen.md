---
title: "OpenOffice Impress gets stuck at startup screen"
date: 2008-01-28
forum: General Help
---

### Post by mathnerd314 on 2008-01-28
Hello,

When I try to start OpenOffice Impress, the progress bar on the orange startup screen gets all the way to the end, but then it doesn't start up. I tried reinstalling OpenOffice from the repositories, but still no luck.

I'm on Ubuntu 7.10.

---

### Post by AnonCat on 2008-01-28
I had the same problem for about two months until I installed a new video driver.  In your xorg.conf file what is listed under the "modules" section? If you only have "glx" you might need more options listed in there.  I think this might be why Impress initially failed to load on my machine. Impress seems like a particularly picky program when it comes to video drivers/settings.

---

### Post by AnonCat on 2008-01-28
Also, and I have no idea if this will help you or not, but this section had newly appeared in my xorg.conf file when Impress finally worked:

Section "Files"
	Rgbpath		"/usr/X11R6/lib/X11/rgb"
EndSection

Here's what my "driver" section looks like:

Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

---

### Post by mathnerd314 on 2008-01-28
Is there a separate "Modules" section? 'Cuz this is all I see:

[FONT="Microsoft Sans Serif"]Section "Files"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection[/FONT]

---

### Post by mathnerd314 on 2008-01-30
Also, I tried opening a few files and it got past the splash screen, but still never opened the file.

It worked perfectly well before, so I don't think it could be my video driver...

---

### Post by Hagar Delest on 2008-01-31
Try to rename your OOo user profile (~/.openoffice.org2), perhaps a configuration file has been damaged.

---

