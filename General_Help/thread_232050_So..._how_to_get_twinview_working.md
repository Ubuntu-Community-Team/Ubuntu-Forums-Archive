---
title: "So... how to get twinview working?"
date: 2006-08-08
forum: General Help
---

### Post by Bou on 2006-08-08
Hiya... I've been struggling with twinview for months now, and I'd like someone to give me a hand to get it to work properly.

My xorg.conf (the part related to the graphics card at least) looks like this:

> Section "Device"
	Identifier	"NVIDIA Corporation NV40M? [GeForce Go 6200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
#	Option		"TwinView" "1"
	Option		"ConnectedMonitor" "CRT,TV"
	Option		"MetaModes" "1200x800, 1200x800;1200x800,1024x768;1024x768,1200x800;1024x768,1024x768;"
	Option		"SecondmonitorHorizSync" "30-50"
	Option		"SecondmonitorVertRefresh" "60"
	Option		"TVStandard" "PAL-B"
	Option		"TwinViewOrientation" "Clone"
	Option		"DigitalVibrance" "1"
EndSection

I am working on a Packard Bell laptop with a 1280x800 screen, and I'd like to have the image show on my widescreen 32" (or so) TV. But when I activate Twinview I get image only on the TV... and on top of that it's not even widescreen. I've tried to change the metamodes to:

> Option		"MetaModes" "1280x800, 1280x800;"

But when I do that I get no image on either screen. So please, could anyone tell me what I'm doing wrong? I'm running on regular xorg, not XGL or th like.

Thanks guys.

---

### Post by orb9220 on 2006-08-08
Don't know if this helps but mine specifically states Option		"TwinView" "on"

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

Hope this helps

---

### Post by Bou on 2006-08-08
> **orb9220 said:**
> Don't know if this helps but mine specifically states Option		"TwinView" "on"

Thanks orb, I'll try that when I can kill my session. Even so, I think the problem is metamode-specific, since twinview technically *is* working, even if not properly.

Any further ideas?

---

### Post by koshari on 2006-08-08
iam hearing you there bou, 

i have tried to get the overlay to work on my nvid card, i dont think its possable to have twinview run the desktop on the PC monitor and the overview going to the tv, as i watch movies on my tv screen and use the PC for working.

ideally i would prefer the PC desktop to work normally (with overlay also)and just the overlay get sent to the tv via s-video.

---

### Post by orb9220 on 2006-08-08
This is at the end of my file don't know if it applies

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

---

