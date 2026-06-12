---
title: "Screen Troubles"
date: 2007-04-22
forum: General Help
---

### Post by Madmoose on 2007-04-22
I would like a screen resolution of "1280x1024" , but all I have are these.   

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
```

If I manually go in, and add this resolution like this. Will it screw something up, or will it work perfectly? Can it be done, and if so how do you do it correctly?

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"720x400"	"640x480"	"0x0"
```

Thanks 

Moose

---

### Post by leg on 2007-04-22
No that will work I had to add 1440 x 900 for mine. I am surprised that that resolution is not there though. My install had that one placed in xorg.conf by default.

---

### Post by Dave54 on 2007-04-22
That **should** work and that's how it's **supposed** to be done, however some people have problems. Usually the virtual screen size is bigger than their actual screen resolution on either their desktop or login screen, allowing them to "scroll" around to see their whole desktop. Report back if you have any problems.

---

### Post by Madmoose on 2007-04-22
It worked!

Thanks. 

Moose

---

