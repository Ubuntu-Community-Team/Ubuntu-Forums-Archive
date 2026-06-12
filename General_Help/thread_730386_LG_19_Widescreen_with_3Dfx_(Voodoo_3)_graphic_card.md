---
title: "LG 19 Widescreen with 3Dfx (Voodoo 3) graphic card"
date: 2008-03-20
forum: General Help
---

### Post by abrazafi on 2008-03-20
Hi All,


I'm running kubuntu 7.10.
Have the graphic card 3Dfx Interactive (Inc. Voodoo3).
I bought the LG 19" LCD Widescreen (L196WTQ)

Nothing on screen, the frequency is out of range.
Tried to play with xorg.conf without success ...
Thanks for helping,
Abdon.

Herewith my /etc/X11/xorg.conf file:



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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	Option	        "EnablePageFlip" "True" 	
        BusID		"PCI:0:15:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	60-90
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"Generic Monitor"
	DefaultDepth	16
        SubSection "Display"
		ViewPort 0 0
		Depth 16
		Modes		"1024x768" "800x600" "640x480"
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
EndSection

---

### Post by abrazafi on 2008-03-20
One more information, the graphic card is working fine with my old screen which is
a Dell 17', so the xorg.conf file is based on this 17' Dell monitor.

Thanks,
Abdon.

---

### Post by Edmund_B3 on 2008-04-29
This may help; maybe not... I have the Voodoo 3 card also and an LG 17" monitor (not widescreen). If I set my resolution to 1024x768 and the refresh rate to 60Hz I get an Out Of Range from the monitor, but if I change the refresh rate to 75Hz it works great. I am running Hardy so I can't tell you exactly where to change the refresh setting in 7.10 but hopefully you know enough to figure that part out. I used the same sections from the xorg.conf that you posted.
If you are thinking about upgrading to 8.04 make sure you keep a copy of your xorg.conf because before I found your post I could only get 800x600.
I am VERY new to Ubuntu.

---

