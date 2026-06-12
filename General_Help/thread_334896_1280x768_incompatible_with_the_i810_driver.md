---
title: "1280x768 incompatible with the i810 driver?"
date: 2007-01-09
forum: General Help
---

### Post by Colby on 2007-01-09
Hi.

I just installed Edgy on my gateway tablet, a cx2610 with an intel 915 chipset and a native resolution of 1280x768. The problem is that the only resolution available, according to the "gnome-display-properties" applet as well as xrandr is 1024x768. I cannot change to the native resolution. A strange thing is that xorg.conf has the proper rez lister for all depths, but the system seems to be ignoring that. If it matters, I'm using the "i810" driver for the intel 915 graphics chipset.

Thihgs look a bit fuzzy and streched at this resolution. How can I change it to the proper 1280x768?

---

### Post by RaZoR-x11 on 2007-01-09
Hey, have you config'd your xorg.conf??

RaZoR

---

### Post by Colby on 2007-01-09
I took a look at it, and it seems that Ubuntu set it up properly, with the correct resolution and driver. That doesn't seem to help, though.

---

### Post by RaZoR-x11 on 2007-01-09
Ok, well this is what it should have in it, 

	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x768" "1024x768" "832x624" "800x600" "720x400" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

Edit: Sorry this one.

---

### Post by RaZoR-x11 on 2007-01-09
replace that in your "xorg.conf" in gedit 

Code: "sudo gedit /etc/X11/xorg.conf"

Save the modified one to your user Dir.

Make a backup off the xorg file

Code: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Then turn off KDE or GDM 

Code: "sudo /etc/init.d/gdm stop" 

Code "sudo /etc/init.d/kde stop"

then goto lvl1 

Ctrl + Alt + F1

username and pass.

sudo cp /home/yourusername/xorg.conf /etc/X11/xorg.conf

 Hope it Help's =)

---

