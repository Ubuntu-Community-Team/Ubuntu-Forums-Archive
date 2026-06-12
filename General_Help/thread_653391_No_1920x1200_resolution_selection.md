---
title: "No 1920x1200 resolution selection"
date: 2007-12-29
forum: General Help
---

### Post by tyrion2323 on 2007-12-29
Howdy folks,

There are a smattering of similar threads, but none of my searches brought up this exact issue:

I have a 24" monitor that I would like to run in 1920x1200.  I am using the newest build of LinuxMint (ubuntu based).

For some reason, I am not given the opportunity to select 1920x1200 :(

Any ideas why?  I am a beginner, and any help would be appreciated :)

/tyrion2323

---

### Post by rune0077 on 2007-12-29
In System > Administration > Screens & Graphics. Have you selected your monitor model from this GUI? If not, try that first.

---

### Post by tyrion2323 on 2007-12-30
Hi Rune,

I did try - the Acer AAL2416W is not listed, and I cannot find linux drivers for it from Acer :(

---

### Post by tyrion2323 on 2007-12-30
Hey Rune,

Just noticed that you're from danmark - I used to live right on Amager :)

---

### Post by rune0077 on 2007-12-30
Okay, from the same list, can't you just select a generic monitor (top of the list) of the size you want it to be? That ought to give you the proper screen resolutions.

> **tyrion2323 said:**
> Hey Rune,

Just noticed that you're from danmark - I used to live right on Amager :)

Cool. I'm from Århus myself, but most of my girlfriends family lives in Copenhagen so I go there often. Planning on moving there sometime this year (2008, that is).

---

### Post by tyrion2323 on 2007-12-30
Hey Rune, believe it or not - I tried that!  My monitor is set as Generic 1920x1200, yet I am not given the option to actually try 1920x1200.  I'm sure there's a way to get this to work (as it has worked in Ubuntu and Kubuntu) but I'm not sure.

I only spent about half a year in Copenhagen, but it was amazing.  I am going to grad school in Europe, so I plan to visit Danmark often!

---

### Post by rune0077 on 2007-12-30
That's pretty odd. There's also a Screen Resolution GUI under System > Preferences. Have you tried setting it there (remember to set the refresh rate to 60). If this doesn't work either, you'll probably have to add the option yourself in your Xorg.conf, in which case you might want help from somebody who actually knows what they're talking about:)

---

### Post by tyrion2323 on 2007-12-30
Hey Rune - I think I'm going to have to add it to xorg.conf myself!  Crap, I have no idea how to do that, lol.

---

### Post by rune0077 on 2007-12-30
Okay, last suggestion. When you choose your monitor under Screen & Graphics and set it as generic, did you remember to tick the little box in the lower left corner that says "Widescreen". 1920x1200 is a widescreen resolution, so if isn't set as such, that's probably why it didn't show up.

---

### Post by dr.silly on 2007-12-30
It's not all that painful.

Firstly and just-in-casely, backup the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Now if you need to go back just
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Open it in gedit
```
sudo gedit /etc/X11/xorg.conf
```

Find the Sreen section. Mine looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 2"
	Monitor		"Generic Monitor"
	DefaultDepth	24                 <- this number
	Option "AddARGBGLXVisuals" "True"
	Option "RenderAccel" "True"
	Option "AllowGLXWithComposite" "True"
	Option "backingstore" "True"
	Option "TripleBuffer" "True"
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1280x1024" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1280x1024" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1280x1024" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1280x1024" "1280x960"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1280x960"
	EndSubSection
	SubSection "Display"        <- this subsection
		Depth		24
		Modes		"1400x1050" "1280x1024" "1280x960" "1920x1200" <-added "1920x1200"
	EndSubSection
EndSection
```

Find your DefaultDepth and browse to the corresponding subsection. Then add your resolution to the end of the Modes line in "".

Restart X11 with CTRL+ALT+BACKSPACE.

Should be there.

---

### Post by tyrion2323 on 2007-12-30
Well, I did that, but my xorg doesn't really look like that :(  I will keep trying!

I did change it around and set my graphics card as the Geforce 7 series.  The screen is actually showing up in the 4:3 ratio instead of trying to stretch to fill my full monitor, which actually looks nicer and crisper.

I'll keep lookin!

---

### Post by tyrion2323 on 2007-12-30
Here's what I've got:

> 
Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Acer AL2416W"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1920x1200"
	Horizsync	31.5-74.5
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Acer AL2416W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1600x1200@60"	"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection


---

### Post by dr.silly on 2007-12-30
see adding modeline

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by rune0077 on 2007-12-30
Just tried this: I changed my screen to Generic, and rather than selecting the size of my screen, I just choose "Plug n' Play" at the very bottom of the list. The I ticked the Widescreen box. This allowed me to set *all* widescreen resolutions, even those my monitor can't actually display. I got 1920x1200 on the list, though my monitor doesn't run that high.

---

### Post by tyrion2323 on 2007-12-30
Wahoo!  I followed Rune's advice and we're working on all cylinders now :)

Thank you everyone :)

---

