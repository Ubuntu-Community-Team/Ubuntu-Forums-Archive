---
title: "Firefox stops drawing webs"
date: 2006-12-17
forum: General Help
---

### Post by dolarsrg on 2006-12-17
Hello everyone!

I'm using Kubuntu Edgy since its release and since that moment I've a problem I can't solve ](*,) 

I prefer using Firefox than Konqueror, but usually, after some minutes of sufing webs with Firefox 2.0 it stops drawing the webs. I mean, it loads them, but it doesn't refresh the view if I dont change the size of the windows. Then I can use the web, but if I click in another Link I have to resize the browser window in order to be able to see the new webpage.

If I click in a Target=_blank link it open a new empty web, then, if I resize the window the page its showed.

Do you have any ideas about the reason?

Thanks in advance!!

---

### Post by dcstar on 2006-12-18
> **dolarsrg said:**
> Hello everyone!

I'm using Kubuntu Edgy since its release and since that moment I've a problem I can't solve ](*,) 

I prefer using Firefox than Konqueror, but usually, after some minutes of sufing webs with Firefox 2.0 it stops drawing the webs. I mean, it loads them, but it doesn't refresh the view if I dont change the size of the windows. Then I can use the web, but if I click in another Link I have to resize the browser window in order to be able to see the new webpage.

If I click in a Target=_blank link it open a new empty web, then, if I resize the window the page its showed.

Do you have any ideas about the reason?

Thanks in advance!!

It may well be a video driver issue, post more details of your hardware.

---

### Post by aysiu on 2006-12-18
You said you prefer Firefox to Konqueror.

But does Konqueror work? Or does it experience this problem as well?

---

### Post by NeoChaosX on 2006-12-18
Actually, I've run into this problem, too. After Firefox has been running for awhile, the browser stops redrawing what's in the viewing area. The URL window shows the new URL, but visually the old page is still being shown. And it's entirely a Firefox problem; never had such a problem with Konqueror or any other browser.

I've found that simply restarting Firefox fixes up the problem, but if it happens while doing important business, it's rather annoying.

---

### Post by jeremy on 2006-12-18
I have the same problem, and have had it on EVERY previous version of (k)ubuntu as well, also have had it with firefox from repos as well as download and install from mozilla.

---

### Post by dolarsrg on 2006-12-18
Ok, thanks a lot!!

Just in case, this is mi config (from xorg.conf):

```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "DRI" "true" 
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	Option "AGPFastWrite" "on"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
# 	InputDevice     "stylus" "SendCoreEvents"
# 	InputDevice     "cursor" "SendCoreEvents"
# 	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

And Konkeror (QT), and other GTK programs seems to work well :(

---

