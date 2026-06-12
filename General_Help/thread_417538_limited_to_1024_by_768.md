---
title: "limited to 1024 by 768?"
date: 2007-04-21
forum: General Help
---

### Post by north zulch computer geek on 2007-04-21
on a g4 (ppc) dual 1GHz, 1.25 gigs of RAM, ATI radeon rage pro 9000, monitor with really good resolution (up to 2048 by 1456 or something like that @ 80 hz).

why can't i get past 1024 by 768 @ 60 hz?

im trying to run cinelerra  so that i can edit movies in HD (yes i do professional work.

seriosly considering switching from final cut on OSX to linux

because of the freakin price.

thanks.

PS can anyone recommend a good **_professional_** HD video editing program for linux or OSX?

---

### Post by mhansen on 2007-04-21
When u installed did you choose a higher resolution when it asked you during the xorg configuration?  If you can, paste me the Screen section of your /etc/X11/xorg.conf.  Thanks.

Did you install the ATI driver btw?


Regards,
Mike

---

### Post by dta116 on 2007-04-21
I too have the same problem....

My file section reads:


Section "Device"

	Identifier	"ATI Technologies Inc Radeon Mobility X700 (PCIE)"

	Driver		"ati"

	BusID		"PCI:1:0:0"

	EndSection

Section "Monitor"

	Identifier	"Generic Monitor"

	Option		"DPMS"
EndSection


Section "Screen"

	Identifier	"Default Screen"

	Device		"ATI Technologies Inc Radeon Mobility X700 (PCIE)"

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

---

### Post by mhansen on 2007-04-21
Well, I'm sorry, but I used Slackware for 12 years, so I'm gonna tell u how to edit the file by hand....someone will help me out here and give me the "Ubuntu way".  :)

Do a sudo pico xorg.conf and where it says:  (if you don't use pico, use whatever you like)

Depth 24

Modes "1024x768" "800x600" "640x480"


add a resolution in front of "1024x768" that u know works for your monitor (and that u want to use), so you might make it look like this:

Depth 24

Modes "1280x1024" "1024x768" "800x600" "640x480"



Regards,
Mike

---

### Post by spankymasterc on 2007-04-21
its sudo gedit /etc/X11/xorg.conf

or u can also do the video card again

sudo dpkg-reconfigure xserver-xorg and when it ask you about the resolution select the one u want and press the space bar so it adds a start 

::cheers::

hit me up if you want

---

