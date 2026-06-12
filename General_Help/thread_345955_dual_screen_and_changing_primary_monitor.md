---
title: "dual screen and changing primary monitor"
date: 2007-01-25
forum: General Help
---

### Post by canucks on 2007-01-25
hi, 

i have ubuntu setup and dual screen working, but i can't seem to change the primary and secondary around.  it thinks my TV is my primary screen and LCD is secondary, i want it the other way around.  it's pretty much a send xorg.conf file from a gentoo installation to this pc :)
it works fine in gentoo, but not here :(

anyways, here's the xorg.conf

```


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "MainLCD"
	Screen      1  "TV" LeftOf "MainLCD"
	InputDevice    "Logitech KB" "CorePointer"
	InputDevice    "Logitech MS" "CoreKeyboard"
EndSection

Section "Files"
   FontPath    "/usr/share/fonts/misc:unscaled"
   FontPath    "/usr/share/fonts/Type1"
   FontPath    "/usr/share/fonts/TTF"
   FontPath    "/usr/share/fonts/corefonts"
   FontPath    "/usr/share/fonts/freefont"
   FontPath    "/usr/share/fonts/sharefonts"
   FontPath    "/usr/share/fonts/terminus"
   FontPath    "/usr/share/fonts/ttf-bitstream-vera"
   FontPath    "/usr/share/fonts/unifont"
   FontPath    "/usr/share/fonts/75dpi:unscaled"
   FontPath    "/usr/share/fonts/100dpi:unscaled"
   FontPath    "/usr/share/fonts/artwiz"
EndSection

Section "Module"
	Load  "glx"
	Load  "extmod"
	Load  "xtrap"
	Load  "record"
	Load  "dbe"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Logitech MS"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Logitech KB"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
#	Option	    "Dev Name" "Logitech USB Receiver"
#	Option      "Dev Phys" "usb*/input0"
#	Option	    "Resolution" "800"
	Option	    "Buttons" "9"
#	Option	    "ZAxisMapping" "11 12"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier	"Samsung713v"
	VendorName	"Samsung713v"
	ModelName	"vs2050vm"
	Option		"DPMS"
	Option		"Metamodes" "1280x1024"
EndSection
	
Section "Monitor"
	Identifier	"TV"
	VendorName	"TV"
	ModelName	"vs2050vm"
	Option		"DPMS"
	Option		"Metamodes" "1280x1024"
EndSection

Section "Device"
	Identifier  "6600GT"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "geForce 6600GT"
	BusID       "PCI:2:0:0"
	Option	    "nologo" "true"
	Option	    "NoBandWidthTest" "true"
	Option	    "VertRefresh"	"DFP:60"
	Option	    "UseDisplayDevice"  "DFP"
	Option	    "MetaModes" "DFP: 1280x1024"
	Screen	    0
	Option "AllowGLXWithComposite" "true"
	Option	"UseEdidDpi" "FALSE"
	Option  "DPI" "96 x 96"
EndSection

Section "Device"
	Identifier  "6600GT-TV"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "geForce 6600GT"
	BusID       "PCI:2:0:0"
	Option	    "nologo" "true"
	Option	    "NoBandWidthTest" "true"
	Option	    "VertRefresh"	"CRT:60"
	Option	    "UseDisplayDevice"  "CRT"
	Option	    "MetaModes" "CRT: 1280x1024"
	Screen	    1
	Option "AllowGLXWithComposite" "true"
	Option	"UseEdidDpi" "FALSE"
	Option  "DPI" "96 x 96"
EndSection

Section "Screen"
	Identifier	"MainLCD"
	Device		"6600GT"
	Monitor		"Samsung713v"
	SubSection	"Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024"
	EndSubSection
	Option      "AddARGBGLXVisuals" "true"
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"6600GT-TV"
	Monitor		"TV"
	SubSection	"Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024"
	EndSubSection
	Option      "AddARGBGLXVisuals" "true"
EndSection

Section "Extensions"
	Option	"Composite"	"Enable"
EndSection




```

thanks

---

### Post by ~LoKe on 2007-01-25
Maybe this isn't the desired result, but change
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "MainLCD"
	Screen      1  "TV" LeftOf "MainLCD"
	InputDevice    "Logitech KB" "CorePointer"
	InputDevice    "Logitech MS" "CoreKeyboard"
EndSection
```
to
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "MainLCD"
	Screen      1  "TV" RightOf "MainLCD"
	InputDevice    "Logitech KB" "CorePointer"
	InputDevice    "Logitech MS" "CoreKeyboard"
EndSection
```

---

