---
title: "Screen display issue"
date: 2007-10-28
forum: General Help
---

### Post by bks on 2007-10-28
I wasn't sure if this post fit better in Gaming & Leisure or Multimedia & Video, so I put it here.  I just got through following [***this***]("https://help.ubuntu.com/community/RadeonDriver#head-229f59879c2a2b6c6635d1e189706d97f836b879") how to and got my direct rendering working.  Now I have all the cool desktop effects enabled and it works great. My problem now is, when I try to play Alien Area my screen is completely distorted, kind of like a fuzzy TV channel. I figure it has something to do with my driver, but before I made the changes I had no hardware acceleration at all (with fglrx). If any one has any thoughts that would be awesome. Thanks.

Here is the Device section of my xorg.conf:
```

Section "Device"
	Identifier	"Radeon Mobility M6"
	Driver		"ati"
	Option          "AGPMode"        "8"
        Option          "AccelMethod"    "XAA" #either XAA or EXA. only "XAA" is supported for some of the cards with "experimental" 3d acceleration
        Option          "ColorTiling"    "on"
        Option          "EnablePageFlip" "true" #only works with accelmethod "XAA"
        Option          "AccelDFS"       "true" #seemed to speed things up using EXA acceleration
        Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
        Option          "DynamicClocks"  "on"   #This is for laptop users, it saves energy when in battery mode.

        Option          "DMAForXv"       "true" #This can speed up movie playback but can in rare cases case instability
        Option          "GARTSize"       "64"   #This is the size of the "GART" that xorg will use.
	BusID		"PCI:1:0:0"
EndSection

```

---

### Post by Fire_Chief on 2007-10-29
You may want to test running Alien Arena without the Desktop Effects enabled. I was having severe video playback problems until I turned off Desktop Effects. Then the video was perfectly smooth.

---

### Post by bks on 2007-10-29
> **Fire_Chief said:**
> You may want to test running Alien Arena without the Desktop Effects enabled. I was having severe video playback problems until I turned off Desktop Effects. Then the video was perfectly smooth.

I did try that, but just tonight I realized that it is not my ATI card, it is my monitor driver that is not properly installed.  I'm thinking that the game either changes to or requires a refresh rate that my screen can't handle and it ends up garbling everything.  Which is good and bad. Good because it means all the time I spent on my graphics card was not in vein and bad because now I have another problem. Thanks for the response.

---

### Post by bks on 2007-10-29
Okay, so I've done quite a bit of digging and now know that my LCD doesn't really have a driver (I was hoping to be able to import an INI file) because Windows uses a PNP driver at startup.  However, I got the part number for the LCD (Gateway 400SD 7004288) maybe that will help. 
Is there anyway I can adjust the refresh rate in Alien Arena? Or how should I tackle this problem? I'm going to keep hunting, but if anyone has an idea that would be great!

---

### Post by Fire_Chief on 2007-10-30
It's a bit of a pain but I'd suggest manually inputting the refresh rates for your monitor into the xorg.conf file. (horizontal and vertical). I've had better luck with that than trying to use the new gui utility. For some reason I can't get the utility to keep or save the settings into my xorg.conf file.

---

### Post by bks on 2007-10-30
> **Fire_Chief said:**
> It's a bit of a pain but I'd suggest manually inputting the refresh rates for your monitor into the xorg.conf file. (horizontal and vertical)

Okay, that's what I figured, but I've had a hard time finding the actual refresh rates.  I tried to find it on Gateway's support site, but only the CRTs and flat panels are listed. I'll keep trying, Thanks!

---

### Post by Fire_Chief on 2007-10-30
I checked the Gateway site and noticed that the display (this is a laptop right?) only does 1024x768 max resolution on the built-in display. Are you running the game at this resolution? Which monitor frequencies are being used by your xorg.conf? You may want to compare them against the settings for the generic LCD 1024x768 monitor listed in the Screens & Graphics control panel (choose a monitor). In any event, the max refresh rate supported for that display is 60Hz (per the Gateway site).

---

### Post by bks on 2007-11-03
> **Fire_Chief said:**
> I checked the Gateway site and noticed that the display (this is a laptop right?) only does 1024x768 max resolution on the built-in display. Are you running the game at this resolution? Which monitor frequencies are being used by your xorg.conf? You may want to compare them against the settings for the generic LCD 1024x768 monitor listed in the Screens & Graphics control panel (choose a monitor). In any event, the max refresh rate supported for that display is 60Hz (per the Gateway site).

I have this in my xorg.conf
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon Mobility M6"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@43"	"1280x960@60"	"1024x768@60"	"1280x1024@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

```

---

### Post by Fire_Chief on 2007-11-03
That is the screen definition. I was referring to the Horizontal and Vertical frequencies listed in the monitor definition of your xorg.conf file. Here is an example```
Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	[B]Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0[/B]
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection
```It may not have any defined if you have a generic monitor definition. You may want to try using an LCD monitor definition for the display ( i.e. LCD 1024x768  ) and see if that changes anything.

---

### Post by bks on 2007-11-03
I switched the monitor to a Generic LCD 1024x768 and here is my xorg:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

```

---

### Post by Fire_Chief on 2007-11-05
Any change in the problem since you modified the monitor definition in your xorg.conf? What resolution do you run the game at (1024x768, 800x600) ? Have you tried running it at a lower rez? Also, have you noticed this problem with any other games that run fullscreen? May want to test with OpenArena just to check.

---

