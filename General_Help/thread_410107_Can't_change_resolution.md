---
title: "Can't change resolution"
date: 2007-04-15
forum: General Help
---

### Post by shironeko on 2007-04-15
I'm installing and configuring Ubuntu on my mother's laptop which has an ATI Graphics card and a wide/panorama screen.

Now I'm at 1024x768 screen resolution, but it all looks streched and unnatural.
The driver installed is ATI, default, and this is Xorg.conf:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
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

Now what I want to do is to use higher resoutions. But whenever I try to change te resolution to a higher one it looks really ugly, everything overlapped, which I suppose has to do with the fact that Xorg is not configured for a higher resolution.

Now, how do I configure xorg, for a higher resolution?
Simply adding the desired resolution to the xorg.conf file, or is there anything else I have to do?

---

### Post by Rospo Zoppo on 2007-04-15
Just add the resolution before the others, for example 
Modes		"1440x900" "1024x768" "800x600" "640x480"
everywhere they appear..

---

### Post by beorn! on 2007-04-15
First you want to open a terminal and type the following command,
"sudo nano /etc/X11/xorg.conf"

Then you want to scroll down to the "screen" section of the config file.

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x768" 
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x768"


For each depth you want to add you desired screen resolution at the beginning of the line Modes       "1280x768"

save the file (control + o) then reboot your machine. If at that point you still do not have the proper resolution displayed find out your exact video driver and exact card and post back.

---

### Post by Wim Sturkenboom on 2007-04-15
Linux users usually don't have to reboot :) Restart your X-server by pressing <ctrl><alt><backspace> while in the graphical environment should do the trick.

---

### Post by Rospo Zoppo on 2007-04-16
> Linux users usually don't have to reboot Restart your X-server by pressing <ctrl><alt><backspace> while in the graphical environment should do the trick.
Yeah, you only need to restart the X server :D

---

