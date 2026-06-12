---
title: "How to turn a widescreen on it's side"
date: 2006-07-05
forum: General Help
---

### Post by jckdnk111 on 2006-07-05
I have a sony vaio with an nvidia video card.
I'm running a second, external monitor along with the laptop's lcd in nvidia's twinview mode.

My new fancy dell 20 inch widescreen is capable of turning 90 degrees so I can view things length-wise if I choose (and I would like to). 

How can I change my setup to allow for this? Any help is appreciated of course ...

Here is my current xorg.conf setup for dual monitors:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40M? [GeForce Go 6200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "TwinView" "on"
        Option          "MetaModes" "1680x1050,1280x800"
        Option          "SecondMonitorHorizSync" "28-80"
        Option          "SecondMonitorVertRefresh" "43-60"
        Option          "TwinViewOrientation" "LeftOf"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40M? [GeForce Go 6200]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by sfink01 on 2006-07-06
jckdnk111,

You should be able to input this into the Device section:

Option "Rotate" "string"

    Enable static rotation support. This option takes effect as soon as the X server is started and will work with older versions of X. This feature is supported on GeForce2 or better hardware using depth 24. This feature does not work with hardware overlays, and emulated overlays will be used instead at a substantial performance penalty. This option is not compatible with the RandR extension. Valid rotations are "normal", "left", "inverted", and "right". Default: off.

Best,

Steve

---

### Post by jckdnk111 on 2006-07-07
sfink01,

That works great! Your advice is well informed ... one thing though, is there a way to only rotate the secondary (widescreen) monitor? My laptop screen is also rotating and is essentially unusable with the rotate option.

Thanks again for your help.

Jon

---

