---
title: "blurry screen on high resolution in gutsy"
date: 2007-10-24
forum: General Help
---

### Post by infinite on 2007-10-24
i just finished upgrading all my computers to gutsy
they all work fine, HP laptop, 2 Mac Minis, 2 Desktops :) except for my work computer :(

I have a wide screen ViewSonic VX2035wm that supports up to 1680x1050 resolution
it used to be working just fine on feisty, but after the upgrade it all looks blurry now ...

lower resolutions look fine, it's only this one that's broken, i suspect it has something to do with the refresh rate (obviously! no?)

I did my homework, searched for similar bugs or forum posts, however all talk about high resolution resulting in a flickering screen, which is NOT what i'm getting, i can see everything on my screen, but it's all blurry ...

i messed around with all the possible screen settings with no hope, then i played around with xorg.conf with no hope either ...

here's what i tried:
- setting custom HorzSync, VertRefresh values based on the manufacturer's specs
- using a custom Modline
- using a custom Modline with different refresh rates
- using ati's binary driver

none worked ... any ideas ?


here's the relevant section of my xorg.conf file:
```

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VX2035wm"
	Option		"DPMS"
	#HorizSync	30-82
	#VertRefresh	50-85
	Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync	
	Modeline "1680x1050_62.00"  152.18  1680 1784 1968 2256  1050 1051 1054 1088  -HSync +Vsync
	Modeline "1680x1050_65.00"  159.84  1680 1784 1968 2256  1050 1051 1054 1090  -HSync +Vsync
	Modeline "1680x1050_70.00"  173.83  1680 1792 1976 2272  1050 1051 1054 1093  -HSync +Vsync
	Modeline "1680x1050_72.00"  178.96  1680 1792 1976 2272  1050 1051 1054 1094  -HSync +Vsync
	Modeline "1680x1050_75.00"  188.07  1680 1800 1984 2288  1050 1051 1054 1096  -HSync +Vsync
	Modeline "1680x1050_80.00"  201.16  1680 1800 1984 2288  1050 1051 1054 1099  -HSync +Vsync
	Modeline "1680x1050_85.00"  214.51  1680 1800 1984 2288  1050 1051 1054 1103  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"VX2035wm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1648x1050_75.00" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

