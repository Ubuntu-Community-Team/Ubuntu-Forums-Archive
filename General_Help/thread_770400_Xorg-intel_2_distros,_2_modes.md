---
title: "Xorg-intel 2 distros, 2 modes"
date: 2008-04-27
forum: General Help
---

### Post by RockDoctor on 2008-04-27
Wondering why I can't get Fedora and Ubuntu to give me the same video mode on my Soyo 20" monitor. xorg.conf files are basically identical (relevant part):
> 
Section "Device"
	Option     "NoAccel"     	"True"
	Identifier  "Card0"
	Driver      "intel" #card0driver
	VendorName  "Intel Corporation"
	BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1680x1050"
    EndSubsection
EndSection


xrandr on Ubuntu reveals the following:
> 
1680x1050 (0x4f)  147.1MHz
        h: width  1680 start 1784 end 1968 total 2256 skew    0 clock   65.2KHz
        v: height 1050 start 1051 end 1054 total 1087           clock   60.0Hz

whereas on Fedora I get
> 
1680x1050 (0x3b)  174.0MHz -HSync +VSync
        h: width  1680 start 1800 end 1976 total 2272 skew    0 clock   76.6KHz
        v: height 1050 start 1053 end 1059 total 1096           clock   69.9Hz

What I want is for Xorg in Ubuntu to use the mode used in Fedora. Can this be made to happen?

---

