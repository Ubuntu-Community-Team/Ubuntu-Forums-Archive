---
title: "problem with my screen"
date: 2007-03-02
forum: General Help
---

### Post by funpop on 2007-03-02
see the attached picture for my problem.

i always get a osd-warning (frequency not in spec) as soon as i turn my computer on.

i played around with kernel options: vga=771 finally gives me this progress bar but not in the resolution and position where it belongs, 773 and 769 just give a black screen until X is starting. (there i dont have any problems with 1024 * 768, 60Hz)

my monitor is a 15" TFT (MD 9383 aa).. cant get more info from google about its specs)
and the graphics card is ati radeon 9500 pro.

that osd warning was always there (already when i just bought that pc from a friend)

if i plug in my tv-out and have the same screen on my tv , i see a wonderful progress bar there.

any ideas how to fix this ?

---

### Post by saneone on 2007-03-02
did u try to enter modes manually in /etc/X11/xorg.conf??

---

### Post by funpop on 2007-03-02
no, this section looks like this at the moment:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Ati Radeon 9500 Pro"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
```

edit and:

> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

---

### Post by saneone on 2007-03-02
Here`s mine Monitor Section for example:

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "Flat Panel 1280x1024"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection



here u have a calculator for sync rates:
[http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html)

maybe it will become useful for you...

BTW. could you please post your "/usr/bin/startx" file? i need it, cuz i deleted it by a mistake :/

---

### Post by funpop on 2007-03-02
thanks, i will try it later.

dont know if this works for you since i use feisty

[http://www.divshare.com/download/179108-d12](http://www.divshare.com/download/179108-d12)

but that file wasnt modified since august 8 2006 or something

edit:

i added modelines for 640*480 800*600 and 1024*768
nothing changed

---

### Post by funpop on 2007-03-04
bump 

is this a problem of the bios-configuration ?

---

