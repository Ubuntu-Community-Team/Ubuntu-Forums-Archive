---
title: "Monitor is native 1280x1024, running it at 1920x1080?"
date: 2007-01-12
forum: General Help
---

### Post by ~LoKe on 2007-01-12
I'm trying to get my LCD's to run at 1920x1080 instead of 1280x1024, but xorg just won't let me.  Is this something I can fix, or am I stuck?

> Section "Screen"
	Identifier			"Default Screen"
	Device				"NVIDIA GeForce 7900GS"
	Monitor				"DELL 1907FP"
	DefaultDepth			24
	SubSection "Display"
		Depth			24
		Modes			"1920x1080" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	Option "TwinView" 		"True"
	Option "TwinViewOrientation" 	"RightOf"   
	Option "UseEdidFreqs" 		"True"
	Option "MetaModes" 		"1920x1080,1920x1080; 1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" 	"DFP"
	Option "ConnectedMonitor" 	"DFP, DFP"
	Option "AddARGBGLXVisuals" 	"True"
EndSection

---

### Post by dcstar on 2007-01-12
> **~LoKe said:**
> I'm trying to get my LCD's to run at 1920x1080 instead of 1280x1024, but xorg just won't let me.  Is this something I can fix, or am I stuck?

If your monitor is "native 1280x1024", why do you think you can run it at a higher resolution?

---

### Post by ~LoKe on 2007-01-12
> **dcstar said:**
> If your monitor is "native 1280x1024", why do you think you can run it at a higher resolution?

Because most monitors can run higher than the native, except there's a bit of quality loss.

---

### Post by chavo on 2007-01-12
Try removing all of the other modes except for 1920x1080.

---

### Post by ~LoKe on 2007-01-12
> **chavo said:**
> Try removing all of the other modes except for 1920x1080.

Sounds like a plan.  I'll report back. ;)

---

### Post by d3v1ant_0n3 on 2007-01-12
I thought LCD monitors native res was also it's maximum?

---

### Post by ~LoKe on 2007-01-12
Guess it appears that way.  I know in Windows you can push it further, but I guess that's not a possibility in Linux?  I can't remember, I haven't been on Windows in some time.

Removing the other modes didn't help. :(

---

### Post by Delkster on 2007-01-12
> **~LoKe said:**
> I know in Windows you can push it further, but I guess that's not a possibility in Linux?

Even if it's possible, without seeing the effect I don't really understand why you'd want that. if the physical display can't show pixels at a resolution higher than the native one, by having the OS  use a "higher" resolution virtually you'd get no more true physical resolution, although you'd appear to be able to have more stuff on the screen. But then, it's hard to say without having ever seen anything like that -- it just doesn't sound very sensible.

Anyway, I have no idea, but whether that's possible may depend on the graphics driver as well, so it may be that your NVidia driver just doesn't support it.

---

### Post by ~LoKe on 2007-01-12
Well, I'm using the latest beta driver and my card is a 7900GS, so I'm pretty sure the problem isn't there.

Oh well, no problem really, I was just curious as to how it would look. ;)

---

