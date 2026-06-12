---
title: "1024 x 768 not showing up???"
date: 2007-04-11
forum: General Help
---

### Post by andrew.46 on 2007-04-11
Hi,

 I am using Xubuntu for only 7 more days and then moving to Feisty (Ubuntu) but I would like to solve one annoying problem. Xfce allows me to use 1024 x 768 as a display setting but calls it 'default'. The live CD Feisty Ubuntu allows me 1024 x 768 and labels it as such. Oddly enough 832x624 does not show up at all.

 I post the relevant section of my xorg.conf below:

```
Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E153FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL E153FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

 Can a wiser man than me tell me what is missing here?

                             Andrew

---

