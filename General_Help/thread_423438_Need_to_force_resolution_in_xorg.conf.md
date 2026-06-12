---
title: "Need to force resolution in xorg.conf"
date: 2007-04-25
forum: General Help
---

### Post by beastmaster on 2007-04-25
Here's my dilemma...

I'm running Feisty. I installed the nvidia drivers for my video card. I'm running an Acer AL2216 through a Neoya X2VGA 2 box (think of it as a KVM switch). When I'm not running through the X2VGA box, my screen resolution is fine (1680x1050). But, if I boot into Ubuntu while the monitor is connected to the X2VGA, I end up with 800x600 resolution.

I can surmise this is because the EDID signals are not transmitted through the X2VGA box. I know I need to set the xorg.conf file so that my video card doesn't try to poll the monitor for it's settings. Here's my xorg.conf file. I've made some changes, but I still end up with 800x600.

Any help would be greatly appreciated.


```

Section "Monitor"
    Identifier     "Acer AL2216W"
    ModeLine       "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Monitor        "Acer AL2216W"
    DefaultDepth    16
    Option         "NoVirtualSizeCheck"
    Option 	   "UseEDID" "FALSE"
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
EndSection


```

---

### Post by beastmaster on 2007-04-26
Answering my own post...

It took a couple of evenings of tinkering, but I got my xorg.conf settings to stick. This post will help anyone else in the same predicament:

[http://ubuntuforums.org/showthread.php?p=129379#post129379](http://ubuntuforums.org/showthread.php?p=129379#post129379)

---

### Post by beastmaster on 2007-04-26
Also, here are the changes I made. 

```
Section "Monitor"
    Identifier     "Acer AL2216W"
    HorizSync	31-101
    VertRefresh	60-160
    # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
    Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Driver         "nvidia"
    Option	"UseEDIDFreqs" "FALSE"
    Option	"UseEDIDDpi" "FALSE"
    Option	"ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Monitor        "Acer AL2216W"
    DefaultDepth    16
    Option	"DPI" "90x88"
    Option	"NoVirtualSizeCheck"
    Option	"UseEDIDFreqs" "FALSE"
    Option	"UseEDIDDpi" "FALSE"
    Option	"ModeValidation" "NoEdidModes"
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024"
    EndSubSection
EndSection

```

---

### Post by yetihehe on 2007-07-27
I've tried everything, but gnome sets 1680x1050@60, but monitor still only displays it as 1280x1024@60 (with shrinking AND some screen fragment is invisible, either top or bottom menu). When I set 1280x1024@75 it works ok. My xorg.conf:
```

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"AGP:1:0:0"
	Screen		0
#        Option		"UseDisplayDevice" "DFP-0"
	Option		"NoLogo"
	Option		"RenderAccel" "true"
	Option		"UseEDIDFreqs"	"FALSE"
	Option		"UseEDIDDpi"	"FALSE"
#        Option		"ExactModeTimingsDVI" "true"
#	Option		"ModeValidation" "DFP-0: NoMaxPClkCheck, NoEdidMaxPClkCheck, AllowNon60HzDFPModes, NoMaxSizeCheck, NoVirtualSizeCheck"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
#	Option		"DPMS"
	HorizSync	31-85
	VertRefresh	60-75
# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
	Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"SyncMaster"
	Option		"UseEDIDFreqs"	"FALSE"
	Option		"UseEDIDDpi"	"FALSE"
	Option		"NoVirtualSizeCheck"
	Option		"DPI"	"90x88"
	Option		"ModeValidation"	"NoEdidModes"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```
Card is gf6800gt and screen is belinea 2225 s1w
Will it work, or will it blend?

---

