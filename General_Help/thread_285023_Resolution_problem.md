---
title: "Resolution problem"
date: 2006-10-26
forum: General Help
---

### Post by ehird on 2006-10-26
Hey - my 'net finally works on ubuntu. Great! Just one problem now...

The resolution max is 1024x768 85hz. I assume I need some drivers, but here lies the problem: Are there any avaliable for SiS Mirage cards? I wouldn't think so, but you never know... :???:

---

### Post by hartunnoo on 2006-10-26
As far I know, yes it only up to 1024*768, I wish to have 1280*1024. But I dont know how to get to that high. :(

---

### Post by ehird on 2006-10-26
I highly doubt that's an actual limit.

---

### Post by CatKiller on 2006-10-26
> **ehird said:**
> The resolution max is 1024x768 85hz. I assume I need some drivers, but here lies the problem: Are there any avaliable for SiS Mirage cards? I wouldn't think so, but you never know... :???:

[http://packages.ubuntu.com/dapper/x11/xserver-xorg-driver-sis](http://packages.ubuntu.com/dapper/x11/xserver-xorg-driver-sis)

You've probably already got this installed. Just edit your xorg.conf to change the Device Driver line to "sis" and add in the resolutions you want to the Screen section and you should be hot to trot.

Good luck.

---

### Post by ehird on 2006-10-26
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"

```
That line? :)

---

### Post by CatKiller on 2006-10-26
> **ehird said:**
> That line? :)

Well, mine looks like ```
Section "Screen"
	Identifier	"LeftScreen"
	Device		"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"Hansol 730E"
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
``` And where mine says > Section "Device"
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nvidia"yours would say something about your graphics card and have Driver     "sis"

Oh, and you can call these things whatever you want, as long as you are consistent in the Identifiers.

---

### Post by ehird on 2006-10-26
Um, I don't see anything in your config about Driver. Sorry if I'm noobish, but I just can't find a line to change the Driver thingsie.

---

### Post by CatKiller on 2006-10-26
Under where is says **Identifier "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"** it says **Driver "nvidia"**. This is the **Device** section.

Resolutions are specified as modes, per colour depth, in the **Screen** section.

---

