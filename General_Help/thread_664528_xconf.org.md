---
title: "xconf.org"
date: 2008-01-11
forum: General Help
---

### Post by thatlondon on 2008-01-11
Hi,

I have ubuntu 7.10 live running on a memory stick.  Everything works fine in persistent mode except the tablet function.  I read on the forums about removing comments on some lines in the xconf.org and when i restart X11 everything works fine.

However when I reboot something is re-writing my xconf.org file replacing the comments.  I guess this may be a feature of the live cd to autodetect graphics hardware and this is fine.  Could someone tell me where in the init files the xconf.org file is created so I can add something to remove the comments if the computer is a tablet PC.

Kind Regards,

Nic

---

### Post by jken146 on 2008-01-11
/etc/X11/xorg.conf

---

### Post by setjahat on 2008-02-10
I did some changes in the xconf.org file (in /etc/X11) because the monitor that I've selected for my laptop, i.e. LCD Panel 1280x800 wouldn't set to 1280x800 but only up to 1024x768. I'm using an Acer Aspire 5550 with 14.1" wide screen and this (1024x768 ) resolution is not right. The changes that I've made:

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Added:

  modeline  "1280x800@60" 65.0 1280 1360 1440 1600 800 768 900 1200 -vsync -hsync

after the line

  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync

and changed:

		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"

to

		Virtual	1280	800
		Modes		"1280x800@60"      "1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"

it worked fine initially but when I restarted the resolution goes back to 1024x768 and the xconf.org file is re-written.

Please help..

---

