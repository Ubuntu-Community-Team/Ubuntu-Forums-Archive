---
title: "Dual Screen With Sony Vaio CR"
date: 2008-06-14
forum: General Help
---

### Post by msk89 on 2008-06-14
Hey everyone, I'm reasonably new to linux and brand new to this forum.  I recently turned my new sony vaio cr into a linux machine (running the new hardy version of ubuntu).  So far Ive been able to get everything working including the webcam which gave me a little bit of trouble and a chance to get to know the command line a little better.  My current project is getting dual screen capabilities up and running.  Running lspci returns 

"00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)"

as my graphics card.  From what I can tell, this card is capable of what I am attempting to do.  Below Ive posted my edited xorg.conf.  The way Ive been attempting to use is the Xinerama method.  I feel like im close, but every time i boot up the machine it says it cant find my graphics card or something like that and I am forced to boot in low res mode.  At this point staring at the low res for so long has given me a migrane that kept me up most of last night so I feel like its time to ask the experts.  Thanks in advance.  


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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "ServerLayout"
	Identifier	"Simple layout"
	Screen	0	"Screen0"
	Screen	1	"Screen1" LeftOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "on"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"card0"
	Driver		"i810"
	BusID		"PCI:00:02:0" 
 Screen      0
Option "MonitorLayout" "DFP,CRT"
Option "HWcursor" "off"
Option "DigitalScreen1" "on"
Option "DDCMode" "True"

EndSection

Section "Device"
	Identifier	"card1"
	Driver		"i810"
	BusID		"PCI:00:02:0"
 Screen      1
Option "DDCMode" "True"
Option "MonitorLayout" "DFP,CRT"  
Option	"HWcursor" "off"

EndSection

Section "Monitor"
	Identifier	"sony"
Modeline "1024x768@75" 85.52 1024 1056 1376 1408 768 782 792 807
	HorizSync	31.5-80
	VertRefresh	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	identifier	"dell"
	Modeline "1024x768@75" 85.52 1024 1056 1376 1408 768 782 792 807
	HorizSync	31.0 - 70.0
	VertRefresh	50.0 - 160.0
	Option		"DPMS"
Endsection

Section "Screen"
	Identifier	"Screen1"
	Device		"card1"
	Monitor		"dell"
	DefaultDepth	24

	Subsection "Display"
		Depth	8
		Modes "1024x768@75" "800x600" "640x480"
	EndSubSection

	SubSection "Display"
                Depth     16
        	Modes   "1024x768@75" "800x600" "640x480"
        EndSubSection

        SubSection "Display"
                Depth     24
        	Modes   "1024x768@75" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"card0"
	Monitor		"sony"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" 
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by msk89 on 2008-06-25
I recently got dual screen working by setting up a virtual screen with xrandr.  A quick google search for virtual screens with xrandr should give you everything you need to reach your dual screen goals (atleast with an intel card)

---

