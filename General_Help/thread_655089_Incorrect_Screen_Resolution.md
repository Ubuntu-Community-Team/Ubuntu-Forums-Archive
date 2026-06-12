---
title: "Incorrect Screen Resolution"
date: 2007-12-31
forum: General Help
---

### Post by Septenary on 2007-12-31
Hello,

A few days ago, I installed **Ubuntu 7.10** Desktop to my USB external hard drive in a dual-boot setup with Windows XP.  Since then, I have been **trying to make Ubuntu display at the correct screen resolution**.  

My monitor, a **Samsung Syncmaster 906BW**, has an optimum resolution of **1440x900@60Hz**.  However, **this resolution does not appear on System > Preferences > Screen Resolution**.  (1280x1024, 1024 x 768, 800 x 600 and 640 x 480 are the options available.)  I have it currently set to 1280x1024@75Hz - the screen is badly offset to the left and stretched.

In an attempt to fix this, I followed several instructions, such as the ones at
**[COLOR="DarkOrange"][https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")[/COLOR]**      
and 
**[COLOR="DarkOrange"][http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")[/COLOR]**.

However, despite **repeatedly editing xorg.conf** and running through "**sudo dpkg-reconfigure xserver-xorg**" several times, I cannot get it to display at 1440x900.

Here is a copy of the relevant part of my xorg.conf:

```
Section "Device"
	Identifier	"nVidia Corporation C51 [GeForce 6150 LE]"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
	Option "UseEdidFreqs" "false"
EndSection
```

I would really like this fixed.  :(   Sorry if I seem inexperienced - this is the first time I have installed Ubuntu.  If anyone has any advice, I'd be very grateful to hear it.  Thanks!

---

### Post by taurus on 2007-12-31
Go into System -> Administration -> Restricted Drivers Manager and install nvidia driver for your graphic card.  You are using generic card right now for your nVidia card.

---

