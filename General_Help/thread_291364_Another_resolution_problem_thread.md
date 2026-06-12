---
title: "Another resolution problem thread"
date: 2006-11-02
forum: General Help
---

### Post by SupremePiracy on 2006-11-02
Hey!

I've been looking at a lot of other screen resolution threads but I can't seem to get my 1280x1024 resolution to work. I've edited my xorg.conf file and it seems to be right. 
My screen worked before I reinstalled Ubuntu and had dapper. I have edgy now.

Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
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
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
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

---

### Post by SupremePiracy on 2006-11-02
Never mind. I fixed it by changing the nvidia driver from nv to nvidia.

---

### Post by dannyboy79 on 2006-11-02
i was going to say that,

---

