---
title: "issues with xorg, please help"
date: 2007-04-26
forum: General Help
---

### Post by Locuss on 2007-04-26
I know this should probably be dealt with by the x.org people, but the ubuntuforums people are a lot nicer.

Right now, I have a 27" flatscreen, widescreen lcd Norcent panel. It has a vga plug in it, and before a very long series of mishaps, worked perfectly with kubuntu 6.10. Even after upgrading to feisty, no problems. Then my mishaps, and my own mistakes(I at least admit they were my own) and now, I'm stuck.

Basically, X now will not start. I tried to fix problems with my scrollwheel, and x then started to fail to work on the widescreen. Basically, I think the hertz is too high. 

First, I need some help with the monitor section from xorg.conf 
```

Section "Monitor"
	Identifier	"hp f1503"
	Option		"DPMS"
EndSection
```

What do I change here?

and this is my screen section

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"hp f1503"
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

I saw somewhere that X -configure would help me, from the console login. I tried that, but one thing, how do I get OUT of X -configure, or set options? All I get is a grey screen, the basic cursor displayed and working.

---

### Post by disturbedite on 2007-04-26
if you know for a fact that monitor is out of range (wrong frequency) then you should have a frequency range section that can be edited.

here is mine for example:
Section "Monitor"
  identifier "Gateway EV70"
  vendorname "Gateway"
  modelname "Gateway EV700"
[I][B]  HorizSync 30.0-70.0
  VertRefresh 50.0-120.0[/B][/I]
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  gamma 1.0
EndSection

---

