---
title: "Widescreen not working - need new video card?"
date: 2007-05-09
forum: General Help
---

### Post by rolfotto on 2007-05-09
I just bought a KDS 22" widescreen LCD and hooked it up to my old computer with an analog cable.  It has an i810 intel integrated graphics card and I have tried everything, editing x.org, 915resolution - and still it stays on 1280x1024 even though I want to set it to 1680x1050 or even just 1440x900:mad: 

It keeps resetting what I put into the 915resolution back to the original settings.  The card could even handle 1900x1440 so I don't understand the problem......

Can anybody help?  I'm starting to think I need a new video card because the bios does not show up correctly on the screen (way too big, cropped off).

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	# 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  	Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050__60" "1440x900__60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050__60" "1440x900__60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050__60" "1440x900__60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050__60" "1440x900__60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050__60" "1440x900__60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050__60" "1440x900__60" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

I tried editting this, but it resets to what it was upon restart:
```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 865G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $3a7
Mode Table Entries: 18

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

---

### Post by NilsE on 2007-05-09
Do a search on auto915resolution on here and try it.  The problem with 915resolution alone is that it is not persistent and auto fixes that by creating a boot script to run 915resolution.

when you run auto915resolution you won't need to install 915resolution so say no to that then  use 5c for the mode  1440 900 (or whatever you want) and them 32 for the resolution. Make sure you say yes to creating the boot script.

Then reboot and see if it worked. You may have to select the resolution in the settings the first time you reboot.

By the way, you can run the auto915resolution as many times as you want it will just create a new boot script each time.

Oh yeah, probably nothing wrong with your card it is the the old intel cards don't report correctly.

If this does not work you can also install the intel version from Synaptic instead of the old i810 driver. Search Synaptic for -intel and you will find it

---

