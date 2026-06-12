---
title: "X crashes on resolution switch; Feisty"
date: 2007-06-06
forum: General Help
---

### Post by boris yeltsin on 2007-06-06
No matter what I have tried, I can't seem to fix this problem. It didn't occur in Edgy, as far as I remember, but it has been occurring in Feisty all the time. 

Whenever I run a game (Ex. WoW in Wine) or any full-screen program, my x crashes and restarts back at the login screen. I have no idea why this is happening. Some games that run at my native resolution (1280x800) don't crash, however when I try to change to a lower resolution in those (IE. 1024 x 768 ) it crashes. 

I have Fiesty Fawn running on a Gateway Laptop with Intel integrated graphics. Here are relevant portions of my xorg: 

```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Intel i810"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i810"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "DRI"
	Mode	0666
EndSection

```

I think I've torn out enough hair fixing this problem, so any help (or insight) would be greatly appreciated.

---

### Post by Crafty Kisses on 2007-06-06
> **boris yeltsin said:**
> No matter what I have tried, I can't seem to fix this problem. It didn't occur in Edgy, as far as I remember, but it has been occurring in Feisty all the time. 

Whenever I run a game (Ex. WoW in Wine) or any full-screen program, my x crashes and restarts back at the login screen. I have no idea why this is happening. Some games that run at my native resolution (1280x800) don't crash, however when I try to change to a lower resolution in those (IE. 1024 x 768 ) it crashes. 

I have Fiesty Fawn running on a Gateway Laptop with Intel integrated graphics. Here are relevant portions of my xorg: 

```

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Intel i810"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel i810"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "DRI"
	Mode	0666
EndSection

```

I think I've torn out enough hair fixing this problem, so any help (or insight) would be greatly appreciated.

You should try backing up your X Server file, and if anything goes wrong you can restore it fast.

---

### Post by boris yeltsin on 2007-06-06
> **Codename said:**
> You should try backing up your X Server file, and if anything goes wrong you can restore it fast.

My xorg.conf or something else? If it's xorg.conf, I have that backed up (and nearly memorized by this point :P)... However, I don't know how a backup would help me in this case.

---

### Post by Crafty Kisses on 2007-06-06
> **boris yeltsin said:**
> My xorg.conf or something else? If it's xorg.conf, I have that backed up (and nearly memorized by this point :P)... However, I don't know how a backup would help me in this case.

This is strange, I've had trouble like this in the past, and I still havn't really solved it. :(

---

### Post by boris yeltsin on 2007-06-06
> **Codename said:**
> This is strange, I've had trouble like this in the past, and I still havn't really solved it. :(

Odd thing is that I remember this not happening just a few weeks ago, I used to be able to switch the resolution all I wanted. Hmm... the only thing that I have changed since then was enabling direct rendering. Could that be the cause? How do I turn it off to test?

---

### Post by boris yeltsin on 2007-06-06
Any other ideas? I'm really at a complete loss here...

---

### Post by gregkise on 2007-06-06
Me too!

It just seemed to start happening recently. Both Enigma and Fizzwizzle crashed X when the resolution tried to change.

-g

---

### Post by Sockerdrickan on 2007-06-06
Wow, you registered Sep 2006 and posted NOW? :P

---

### Post by boris yeltsin on 2007-06-06
> **gregkise said:**
> Me too!

It just seemed to start happening recently. Both Enigma and Fizzwizzle crashed X when the resolution tried to change.

-g

Did you do anything to try and change your system at this time? Maybe we have a common problem...

I'm really hoping this can be fixed, it's the only thing preventing me from fully enjoying Ubuntu's bounty. :p

---

### Post by boris yeltsin on 2007-06-07
Sorry to bump...

---

