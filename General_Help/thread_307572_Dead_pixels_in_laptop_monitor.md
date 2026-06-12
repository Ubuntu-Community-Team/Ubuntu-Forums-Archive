---
title: "Dead pixels in laptop monitor"
date: 2006-11-26
forum: General Help
---

### Post by Mimsy on 2006-11-26
What the title says. I seem to have killed a number of pixels in a small square area near the center of my laptop monitor. A forum search took me to a thread that talked about editing /etc/X11/xorg.conf so I made a backup (also strongly recommended in the same thread) and opened it in gedit, and found, among other things, this:

> 
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

I'm not sure what to edit though, or how, or even if this will solve the problem. Thoughts and suggestions are welcome.

Thanks,
Mimsy

---

### Post by bigken on 2006-11-26
I once read somewhere if you rub the area with the dead pixels sometimes they will vanish but in the real world I don''t think there is a cure for dead pixels :-k

---

### Post by ~LoKe on 2006-11-26
Rub them GENTLY with a q-tip.

---

### Post by 56phil on 2006-11-26
Try a different, other than native, resolution. I have a damaged monitor and that helps.

---

### Post by Mimsy on 2006-11-26
I played around with the resolutions, and it seems to have helped. After switching between a few different ones, I went back to the original, and the dead pixels are gone. Clearly, they were only mostly dead.

Thanks!

/Mimsy

---

