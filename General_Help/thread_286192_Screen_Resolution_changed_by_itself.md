---
title: "Screen Resolution changed by itself"
date: 2006-10-27
forum: General Help
---

### Post by justin on 2006-10-27
I recently tried to change the screen resolution for another user on my computer to 1024x768. I didnt like the look of it, so I changed it back to 1280x1024, and enlarged the fonts to make it easier for them to read. However, when I logged out, the GDM resolution was at 640x480, and when I logged in with my user name, my desktop resolution was at 640x480, and it was also the only option. I restarted, and it still only lets me choose 640x480. Here is part of my xorg.conf file:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"Acer AL1715"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Any suggestions for getting me back to 1280x1024? It worked just fine until I tried changing resolutions...

---

### Post by tzulberti on 2006-10-27
You could change the resolution by:
sudo dpkg-reconfigure xserver-xorg

Or once you are logged into Gnome, in System -> Preferences -> Screen Resolution.

---

