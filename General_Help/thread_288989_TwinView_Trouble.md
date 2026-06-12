---
title: "TwinView Trouble"
date: 2006-10-30
forum: General Help
---

### Post by Liehann on 2006-10-30
Hi,

I'm having trouble getting twinview to work and would appreciate some help.

I have gone through many web sites and posts but none of them have helped.

The problem is at login twinview seems to be detected mostly correctly (the screens are the wrong way round) but after logging in the second monitor goes black.

A similar issue I had was before I entered the correct values for my monitor's horz and vert refresh the login screen would display in the correct resolution, and after logging in the screen would drop to a lower resolution. After correcting xorg.conf I used System->Preferences->Screen Resolution to set the correct resolution (the correct resolution had not been an option before).

So the first issue is getting both monitors to work after I've logged in. The second issue is monitor placement. The current setup is like this:
[DVI Blank] [VGA Primary]
where as the desired setup is:
[DVI Primary] [VGA Secondary]

Here are the screen / device / monitor / server sections of my xorg.conf file:
```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		0
	Option		"TwinView"	"on"
	Option		"NoPowerConnectorCheck"
	Option		"MetaModes"	"1280x1024,1280x1024; 1280x1024,NULL"
	Option		"SecondMonitorHorizSync"	"30-82"
	Option		"SecondMonitorVertRefresh"	"50-85"
	Option		"TwinViewOrientation"	"LeftOf"
EndSection

Section "Monitor"
	Identifier	"ViewSonic VP191s"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"ViewSonic VP191s"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0	0
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0	"Default Screen"	0	0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option	"Xinerama"	"Off"
EndSection

```

Any assistance will be appreciated!

Regards,
Liehann

---

### Post by krismatth3 on 2006-10-30
> Option		"MetaModes"	"1280x1024,1280x1024; 1280x1024,NULL"

What's with "1280x1024,NULL"? Try removing that. As for the orientation, trying swtiching "TwinViewOrientation" to "RightOf."

---

### Post by Liehann on 2006-11-01
Thanks - that was the problem.

I read on a post somewhere that having a setting with a null is useful because it is used as a fallback if one of the monitors is not plugged in. I added it and completely forgot about it!

I'm still having trouble getting my orientation correct. I want the login screen and menus to appear on the left monitor, not the right.
I've played with different combinations of TwinViewOrientation but I can't get it to work.

Any further suggestions?

Regards,
Liehann

---

### Post by krismatth3 on 2006-11-01
I suspect the login screen/etc are appearing on what the driver considers to be the main monitor. I'm not sure how to do it software wise, but one possible solution: physically change which monitor is connected to which output, and then swap the twinview orientation. 

(Twinview configuration options: [http://akamai-download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-g.html](http://akamai-download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-g.html) )

---

