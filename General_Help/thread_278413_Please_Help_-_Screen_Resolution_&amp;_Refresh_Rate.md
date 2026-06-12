---
title: "Please Help - Screen Resolution &amp; Refresh Rate"
date: 2006-10-16
forum: General Help
---

### Post by pluto1111 on 2006-10-16
I cannot set my screen resolution to 1024 X 768 @ 85 hz; the best I can do is 1024 X 768 @ 75 hz. I'm using a Spectrum 9Glr monitor, and an Intel i740 video card. I reconfigured xserver, and below is what I have set in my xorg.conf file.
Please help!

Thank you.

```
Section "Monitor"
	Identifier	"AOC Spectrum 9Glr"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i740"
	Monitor		"AOC Spectrum 9Glr"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

```

---

