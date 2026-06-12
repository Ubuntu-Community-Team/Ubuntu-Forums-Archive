---
title: "I've been having a world of problems since upgrading..."
date: 2007-10-26
forum: General Help
---

### Post by ogwilson on 2007-10-26
This is like the first time i've ever had problems upgrading.

Well, I had a very normal display in 7.04 FF after configuring the display in the xorg files or whatever they're called. So after I upgrade, i get alot of bleeding on items, particularly when the desktop is showing. My refresh rate makes my screen very hard to work on, as i cant set it higher than 60. Whenever i choose my monitor and video display (which were magically reset after the update) I am told to restart. After the restart, I get a message saying that the OS will boot up in low graphics mode because I chose the wrong drivers/display settings. So I'm stuck on 1280x1024 @ 60hz refresh rate and i can't change it without getting any problems. im almost convinced that this upgrade is doing me more foul than it is good.

Well anyone, does anyone think they can help me? Please? It works perfectly on my laptop, but not on my desktop. Here are my specs:

AMD Athlon 64 3200+ Processor 2.0ghz rated @ 3.2ghz
1.5 gigs of Ram
ATI Radeon Xpress 200 integrated graphics @ 128megs shared

And my monitor is a CRT 19 inch ViewSonic E90. It's native resolution is 1280x1024 and can go up to 1600x1200.

It worked fine in 7.04 and earlier, but now all of a sudden im just having a ton of problems.

---

### Post by ogwilson on 2007-10-26
bump please.

---

### Post by #Reistlehr- on 2007-10-26
copy and paste you xorg.conf file

---

### Post by ogwilson on 2007-10-26
ok, here's my entire xorg.conf file.

> Section "Files"
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
	Identifier	"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
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

### Post by #Reistlehr- on 2007-10-26
I'm not going to be much help since i don't have an ATI card, but check out the new ATI drivers that were released a few days ago. Hopefully that will do some good. A lot of people said it fixed a few problems for them.

---

### Post by ogwilson on 2007-10-27
yea i checked em out but they did more bad than good. i just disabled the xgl-xserver stuff and used proprietary drivers (but i cant use desktop effects now). Oh well, desktop effects arent that important for me.

---

