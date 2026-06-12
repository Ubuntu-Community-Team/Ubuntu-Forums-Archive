---
title: "Screen Resolution wont change"
date: 2007-02-08
forum: General Help
---

### Post by afnola on 2007-02-08
Edit; Solution found; fglrx drivers installed and inserted in xorg.conf

Hello,

I just recently tried switching back to ubuntu (edgy) but for some reason I cant change my screen resolution.  I tried editting my xorg.conf file to no avail and whenever I change it via System --> Screen Resolution it just logs me off and I log back in with the same resolution of 1600x1200.  I never had these problems when I used to have breezy.  Any suggestions?  My xorg.conf file is below (the unedited version, well part of it)  Thanks in advance

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"vesa"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL P991"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"DELL P991"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

ETA - Im running ATI x800 video card.

---

