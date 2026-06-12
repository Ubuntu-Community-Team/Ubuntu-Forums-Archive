---
title: "No graphics when trying Live CD"
date: 2007-11-09
forum: General Help
---

### Post by intoit on 2007-11-09
I boot with the Live CD and can't get any graphics, even when using safeboot. My card is NVidia FX 5500 256 PCI.
anything special needs to be done?
thanks

---

### Post by yoyo007 on 2007-11-21
i had the same problem with the same card this is what i did. 
i have an integrated video card i used to install ubuntu. When it got installed i booted up then i changed my xorg.conf file. I changed from my integrated intel card to my nvidia card then changed my device in my screen section. then i shutdown and inserted the card and it seemed to work just fine. then ubuntu asked if i wanted to use the nvidia rescricted driver. I installed the driver then everthing has been good after this. 


Section "Device"
	Identifier	"Nvidia 5500"
	Driver		"nv"
	Busid		"PCI:1:0:0"
	Videoram	256000
	Option		"UseFBDev"	"false"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia 5500"
	Monitor		"L17AAM"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection

your busid may be different just change the middle number. I think this depends on what slot the card is in.

---

