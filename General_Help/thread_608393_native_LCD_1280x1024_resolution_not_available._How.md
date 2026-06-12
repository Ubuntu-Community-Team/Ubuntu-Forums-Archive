---
title: "native LCD 1280x1024 resolution not available. How to fix?"
date: 2007-11-09
forum: General Help
---

### Post by gregconquest on 2007-11-09
I have long had a few problems with ubuntu and my video setup. Could someone help me figure this out, please?

I have an MSI (nVidia) GeForceFX5700Ultra 128MB DDR3 card connected via DVI to a Eizo FlexScan L465 monitor.
[http://www.eizo.com/SUPPORT/discontinued/lcd/l465.asp](http://www.eizo.com/SUPPORT/discontinued/lcd/l465.asp)
(I can't find the specs for the video card...)

Ubuntu's "Screen and Graphics Preferences" has settings for neither one of these (graphics card is currently listed as nv - nVidia Riva 128, RIVA TNT, GeForce, nForce, and QUADRO cards). And my resolution is too low. Can I add my specific devices in somehow? I am currently limited to running at 1024x768, but the monitor's native resolution is 1280x1024.

Here is my xorg.conf. It looks like a mess to me, but I've been unable to figure out how it should look.

```
Section "Device"
	Identifier	"NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
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
EndSection
```

This is all under ubuntu 7.10. I have installed linux-restricted-modules, but I am not using any restricted drivers yet:
[http://ubuntuforums.org/showthread.php?t=597117]("http://ubuntuforums.org/showthread.php?t=597117")

Thank you for any help.
Greg Conquest

PS I've tried the online modeline generators, but the first one gave me little info on how to add the lines in, and the second one gave me a warning about the horizontal refresh rate being too low, but there was nothing suggested as to what to do about it. And I don't know how much of this all has changed with the new ubuntu video system (restricted drivers, compiz, and gui video settings).

---

### Post by omrsafetyo on 2007-11-10
every line that says

```
Modes		"1024x768" "800x600" "640x480"
```

should be changed to

```
Modes		"1280x1024" "1024x768" "800x600" "640x480"
```

As always, when changing xorg.conf, make a backup before making changes.

```
sudo cp xorg.conf xorg.conf.orig
```

---

### Post by gregconquest on 2007-11-10
Thanks for that. That was easy. I made the changes (posted below), and rebooted, but **it seems to have made no difference**. *System - Administration - Screens and Graphics* still has the same 1024x768 upper limit, and my screen is still displaying at 1024x768.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV36.1 [GeForce FX 5700 Ultra]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

