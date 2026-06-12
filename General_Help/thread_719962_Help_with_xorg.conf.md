---
title: "Help with xorg.conf"
date: 2008-03-09
forum: General Help
---

### Post by rift400 on 2008-03-09
Hi
I've got a Dell Inspiron 710m which I've just set up Ubuntu Gutsy on (yes I'm more or less a beginner, please be nice if I've over simplified). I've been fiddling with my graphics settings trying to set up a secondary monitor. That seems to have worked with the graphics interface. Now I've got 2 monitors with 1024x768 res instead of the 1280x768 that I want. The graphics interface doesn't seem to want to let me switch up to the higher resolution (option isn't available). 

I've read multiple threads trying to sort out the problem. I've tried a whole bunch of different solutions... none of which have worked. 

dpkg-reconfigure just fixes up one screen and I can't use the second monitor
when I edit xorg.conf it just doesn't look like any of the ones already posted. Anyway... I was wondering if I could edit the xorg file here:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1024x768 Laptop Display Panel"
	Horizsync	31.5-48.5
	Vertrefresh	59.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
```

To add a modeline "1280x768@60" in the section "monitor". And if so what numbers do I add to it? Any ideas?

Cheers
Justin

---

### Post by kuja on 2008-03-10
I would probably have things set up like this:

```
Section "Monitor"
	Identifier	"Default Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1024x768 Laptop Display Panel"
	Horizsync	31.5-48.5
	Vertrefresh	59.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Monitor"
        Identifier    "Secondary Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
           Identifier     "Secondary Screen"
           Device        "Intel Corporation 82852/855GM Integrated Graphics Device"
           Monitor       "Secondary Monitor"
           Defaultdepth	24
                       SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"640x480@75"	"640x480@72"	"640x480@60"
                        EndSubSection
EndSection

Section "ServerLayout"
         Identifier "Default Layout"
         Screen "Default Screen"
         Screen "Secondary Screen" RightOf "Default Screen"
         ...
EndSecton
```

I can't guarentee that this will work, but it should definitely be a step in the right direction - if you intend to be using this second monitor all the time - else, you should probably be looking into xrandr (I've neverr had much luck with it, but it looks like the an appropriate tool.

---

