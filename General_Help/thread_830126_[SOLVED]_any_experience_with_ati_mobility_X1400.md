---
title: "[SOLVED] any experience with ati mobility X1400?"
date: 2008-06-15
forum: General Help
---

### Post by argail1980 on 2008-06-15
Hi everyone,

I have a LG Laptop with an ATI X1400 video card. I just installed the latest proprietary driver and tried compiz. Didn't work at first, because my diver was blacklisted, until I tried this:

[http://ubuntuforums.org/showthread.php?t=765875]("http://ubuntuforums.org/showthread.php?t=765875")

(I should have looked into this forum before)

What I'd like to know if somebody has experience with the combination of proprietary fglrx driver, ati x1400 and compiz. Any crashes, damages?

---

### Post by Mega_Mike on 2008-06-16
I have been using an ATI Mobility x1400 in my Dell Inspiron 6400 (e1505) with Ubuntu Fiesty, Gutsy and now Hardy.  So far performance has been pretty smooth, especially now in Hardy.  It took me a while to get my xorg.conf just right (I'll post it in case it will help).  The parts you want to pay attention to are Section "Device" and Section "Extensions".
```
#
# xorg.conf for Dell Inspiron 6400 (E1505).  
#

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier  "ATI Radeon Mobility x1400"
	Driver      "fglrx"
	VendorName  "ATI"
	BoardName   "ATI Radeon (fglrx)"
	Option	    "DRI" "true"
	Option	    "XAANoOffscreenPixmaps" "true"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	### Experimental Options
        Option      "Textured2D" "on"
        #Option      "TexturedXRender" "on"
        #Option      "BackingStore" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	DisplaySize  410	310
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Radeon Mobility x1400"
	Defaultdepth	24
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "Extensions"
	## For Textured2d and Textured XRender
        Option      	"RENDER" "On"
	Option		"Composite"	"On"
	Option		"XVideo"	"On"
EndSection

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	#Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

---

### Post by argail1980 on 2008-06-17
Thanks,

is there a Documentation where one can find these options? I'd like to understand them better. I wonder what the default values are, because my card works fine too without any of these (except "XAANoOffscreenPixmaps" "true"). I just had to tell compiz to use the driver although it is blacklisted. I also wonder why it was blacklisted. 

But If the card works good for you with compiz and all, I trust, that it at least will do no damage to my system

---

### Post by morgengenuss on 2008-06-17
i have a x1400 in a dell inspiron 9400. been using it since breezy and i have to say that ati's drivers have improved a lot since then.
i know people are always picking on ati because nvidia simply has better support (at least until now), but i think they're trying hard.

anyways, i didn't run into any particular problems with the card.

concerning your confusion with the blacklisted state of the driver: if you install the most recent (or simply a more recent) version of the driver from the ati-site you have to blacklist ubuntu's version of the proprietary driver. that's all.

---

### Post by motopaddy on 2008-06-17
I have Hardy running on my Acer laptop with a X1400 card. No problems, using the restricted drivers. Everything works perfect for me

---

### Post by argail1980 on 2008-06-17
ok, I still run gutsy. At some point I will upgrade tu hardy too, but at the moment the laptop has to run stable, because I need it for work. 

Conclusion: no serious problems with that driver

Thanks to you all...

---

### Post by executive on 2008-06-20
i was having major choppy/stuttering video problem while playing 720p files on my E1505/X1400.. 

but after making changes to my xorg.conf per Mega_Mike's instructions above, im now able to watch 720p vids with no problem. in window mode the video flashes like crazy, but once in full screen it work great.. thanks Mega_Mike!!!

---

### Post by mtbsoft on 2008-06-23
> **argail1980 said:**
> ok, I still run gutsy. At some point I will upgrade tu hardy too,
I had some issues (couldn't get Compiz going) when I upgraded from Gutsy to Hardy but doing a clean install sorted them all.  I also have an Inspiron 9400 with the 1400.

---

