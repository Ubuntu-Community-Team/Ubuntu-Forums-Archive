---
title: "Need some fresh eyes on my xorg.conf please"
date: 2006-10-14
forum: General Help
---

### Post by lonelypauly on 2006-10-14
ive just switched over from ubuntu dapper 32bit to kubuntu 64bit and have had no luck getting both monitors working...hopefully im overlooking something simple enough, as i had it working fine with ubuntu dapper...i have a geforce 6800 ultra (PCI-E) with two Hanns-G JW199D LCD monitors.

my desktop wont load using the config file below.  using the regular/backed up config, my 2nd monitor displays a pattern that looks something like a rom check on an old video game...so i know its working.

any help would be great, thanks.

> 
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"UseFBDev""true"
	Option "TwinView"
Option "TwinViewOrientation" "RightOf"
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024, 1440x900; 1280x1024, 1440x900"
EndSection

Section "Monitor"
	Identifier	"JW199D"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	50-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Monitor		"JW199D"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by aeon on 2006-10-14
Try adding the modelines of your monitors to the xorg.conf, you can get them from the xorg log or from the [online modeline generator]("http://www.bohne-lang.de/spec/linux/modeline/"). They're supposed to be calculated autamagically in xorg, but it might help anyway.. 
Also make shure you have the nvidia drivers installed, nv didn't work with twinview for me atleast..

Here's my xorg.conf (or a snippet of it anyway..) if you need it for comparison:
```

Section "Monitor"
  DisplaySize  340 270
  HorizSync    30-80
  Identifier   "Monitor[0]"
  ModelName    "ACER AL1715"
  Option       "DPMS"
  VendorName   "ACR"
  VertRefresh  43-75
  UseModes     "Modes[0]"
EndSection


Section "Modes"
  Identifier   "Modes[0]"
  Modeline      "1280x1024" 134.72 1280 1368 1504 1728 1024 1025 1028 1068
  Modeline      "1280x1024" 114.54 1280 1360 1496 1712 1024 1025 1028 1062
EndSection


Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1280x1024"
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x1024"
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x1024"
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1280x1024"
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x1024"
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection


Section "Device"
  BoardName    "GeForce 6600/GeForce 6600 GT"
  BusID        "1:0:0"
  Driver       "nvidia"
  Identifier   "Device[0]"
  #Option       "NvAGP" "2"
  #Option       "NvAGP" "0"
  #Option       "NvAGP" "3"
  #Option       "NvAGP" "1"
  Option       	"usevnc" "no"
  #Option 	"RenderAccel" "true"
  Screen       0
  VendorName   "NVidia"
  Option "TwinView" "true"
  Option "SecondMonitorVendorName" "ACR"
  Option "SecondMonitorModelName" "ACER AL1715"
  Option "SecondMonitorHorizSync" "30-80"
  Option "SecondMonitorVertRefresh" "43-75"
  Option "MetaModes" "1280x1024, 1280x1024"
  Option "TwinViewOrientation" "RightOf"
  Option "ConnectedMonitor" "dfp,dfp"
EndSection


Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  Option       "Clone" "off"
  Screen       "Screen[0]"
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection
```

---

