---
title: "what is wrong with my xorg.conf? Resolution troubles"
date: 2007-09-23
forum: General Help
---

### Post by wilsonsamm on 2007-09-23
Hello everyone!
I'm having a spot of bother with my computer because it refuses to let me use any resolution higher than 640x480. It has done in the past, but then I changed monitor (which I know to be capable of up to 800x600) and now I can't see at any resolution higher than 640x480.

I'm using the i810 driver.

Anyone know what the problem could be?

From my /etc/X11/xorg.conf
Section "Device"
	Identifier	"Intel Corporation 82810 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810 CGC [Chipset Graphics Controller]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by Lord Illidan on 2007-09-23
Try running this command, please :  sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by wilsonsamm on 2007-09-23
Ah, it worked, thanks.
What does this command do to which configuration files?

---

### Post by Lord Illidan on 2007-09-23
It basically rebuilds your /etc/X11/xorg.conf

---

