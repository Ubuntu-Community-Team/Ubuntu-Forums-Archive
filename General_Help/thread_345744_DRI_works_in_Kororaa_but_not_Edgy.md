---
title: "DRI works in Kororaa but not Edgy"
date: 2007-01-24
forum: General Help
---

### Post by summersab on 2007-01-24
Alright, so I have a Dell Latitude with an ATI Radeon Mobility 7500 LW and Edgy. I have been trying to put Beryl with AIGLX on it. However, no go. Direct Rendering in glxinfo yields "No." So, for kicks, I booted Kororaa 0.3, a LiveCD with AIGLX and Compiz Official on by default. It worked like a charm and gave Direct Rendering = Yes. So, I thought that perhaps if I copied the xorg.conf from Kororaa and ran it in Ubuntu, it would work. X started fine, but no Beryl and certainly no Direct Rendering in glxinfo. Below is my xorg. What do I do? How do I get Direct Rendering to work and/or grab the required config from the Kororaa to slap onto Edgy?  Beryl HAS to work on this lappy, but in Ubuntu, HOW?

Section "ServerLayout"
	Identifier	"X.Org Configured"
	Screen	0	"Screen0" 0 0
	InputDevice	"Keyboard0" "CoreKeyboard"
# PS/2 Mouse not detected
# Serial Mouse not detected
	InputDevice	"USB Mouse" "AlwaysCore"
	InputDevice	"Synaptics" "AlwaysCore"
	Option		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option	"AllowMouseOpenFail" "true"
	
EndSection

Section "Extensions"
	Option         "Composite"   "Enable"
EndSection

Section "Files"
	FontPath	"/usr/share/fonts/util"
	FontPath	"/usr/share/fonts/encodings"
	FontPath	"/usr/share/fonts/misc"
	FontPath	"/usr/share/fonts/local"
	FontPath	"/usr/share/fonts/terminus"
	FontPath	"/usr/share/fonts/corefonts"
	FontPath	"/usr/local/share/fonts"
	FontPath	"/usr/share/fonts/default"
	FontPath	"/usr/share/fonts/TTF"
	FontPath	"/usr/share/fonts/type1"
	FontPath	"/usr/share/fonts/100dpi"
	FontPath	"/usr/share/fonts/75dpi"
	FontPath	"/usr/share/fonts/arphicfonts"
	FontPath	"/usr/share/fonts/jisx0213"
	FontPath	"/usr/share/fonts/shinonome"
	FontPath	"/usr/share/fonts/baekmuk-fonts"
	FontPath	"/usr/share/fonts/kacst-fonts"
	FontPath	"/usr/share/fonts/sgi-fonts"
	FontPath	"/usr/share/fonts/unfonts"
	FontPath	"/usr/share/fonts/default/ghostscript"
	FontPath	"/usr/share/fonts/xfonts-cronyx-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-cp1251-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-isocyr-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8r-misc"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-100dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-75dpi:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-misc:unscaled"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-100dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-75dpi"
	FontPath	"/usr/share/fonts/xfonts-cronyx-koi8u-misc"
EndSection

Section "Module"
	Load	"ddc"
	Load	"vbe"
#	Load	"GLcore"
	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
	Load	"bitmap"
	Load	"type1"
	Load	"freetype"
	Load	"record"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver	"kbd"
	Option	"CoreKeyboard"
	Option	"XkbRules" "xorg"
	Option	"XkbModel" "pc104"
	Option	"XkbLayout" ""
	Option	"XkbOptions" "grp:toggle,grp_led:scroll"
	Option	"XkbVariant" ",winkeys"
EndSection

Section "InputDevice"
	Identifier	"Serial Mouse"
	Driver	"mouse"
	Option	"Protocol" "Microsoft"
	Option	"Device" "/dev/ttyS0"
	Option	"Emulate3Buttons" "true"
	Option	"Emulate3Timeout" "70"
	Option	"SendCoreEvents"  "true"
EndSection

Section "InputDevice"
	Identifier	"PS/2 Mouse"
	Driver	"mouse"
	Option	"Protocol" "IMPS/2"
	Option	"Device" "/dev/misc/psaux"
	Option	"Emulate3Buttons" "true"
	Option	"Emulate3Timeout" "70"
	Option	"SendCoreEvents"  "true"
	Option	"ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier	"USB Mouse"
	Driver	"mouse"
	Option	"Device" "/dev/input/mice"
	Option	"SendCoreEvents" "true"
	Option	"Protocol" "IMPS/2"
	Option	"ZAxisMapping" "4 5"
	Option	"Buttons" "5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics"
	Driver	"synaptics"
	Option	"Protocol" "event"
	Option	"Device" "/dev/input/event2"
	Option	"LeftEdge" "1900"
	Option	"RightEdge" "5400"
	Option	"TopEdge" "1900"
	Option	"BottomEdge" "4000"
	Option	"FingerLow" "25"
	Option	"FingerHigh" "30"
	Option	"MaxTapTime" "180"
	Option	"MaxTapMove" "220"
	Option	"VertScrollDelta" "100"
	Option	"MinSpeed" "0.02"
	Option	"MaxSpeed" "0.10"
	Option	"AccelFactor" "0.0010"
	Option	"SHMConfig" "on"
EndSection

# Auto-generated by mkxf86config

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync    28.0 - 96.0
	VertRefresh  50.0 - 75.0
EndSection

Section "Device"
	### Available Driver options are:-
	# sw_cursor is needed for some ati and radeon cards
Option "sw_cursor"
	#Option     "hw_cursor"
	#Option     "NoAccel"
	#Option     "ShowCache"
	#Option     "ShadowFB"
	#Option     "UseFBDev"
	#Option     "Rotate"
	Identifier  "Card0"
	# The following line is auto-generated by x11-misc/mkxf86config
	Driver      "radeon"
	VendorName  "All"
	BoardName   "All"
#	BusID       "PCI:1:0:0"
	Option      "XAANoOffscreenPixmaps" "true"
	Option      "DRI"     "true"

EndSection

Section "Screen"
	Identifier	"Screen0"
	Device	"Card0"
	Monitor	"Monitor0"
	DefaultColorDepth 24
	SubSection "Display"
		Depth	1
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth	32
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

---

### Post by summersab on 2007-01-25
I am SUCH a MORON!!! I had the fglrx proprietary driver installed, and it conflicts with the open source radeon driver. You have to uninstall fglrx by doing:

sudo modprobe -r fglrx
sudo apt-get remove xorg-driver-fglrx

and occasionally (mine errored out at "rmdir: directory not empty"; not sure if this is actually necessary, but why not?)
sudo rm -r /usr/lib/fglrx

Enjoy, all ye poor ATI owners!!!

---

