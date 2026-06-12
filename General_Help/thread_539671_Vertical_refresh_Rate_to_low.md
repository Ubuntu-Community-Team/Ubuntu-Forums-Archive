---
title: "Vertical refresh Rate to low"
date: 2007-08-31
forum: General Help
---

### Post by dariem on 2007-08-31
Vertical refresh Rate to low 61Hz comparing with MS XP 85Hz using same configuration. Why?

I've xorg.conf:
```
Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"DiamondPlus7"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"DiamondPlus7"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

```

---

### Post by z0mbie on 2007-08-31
Under the Monitor section specify your displays manufactures specs for refresh rates:
```

Section "Monitor"
	Identifier	"DiamondPlus7"
	Option		"DPMS"
EndSection
```
[B]
Example:
[/B]
```
Section "Monitor"
    Identifier     "Generic"
    HorizSync       28.0 - 80.0
    VertRefresh     48.0 - 75.0
    Option         "DPMS"
EndSection

```

---

