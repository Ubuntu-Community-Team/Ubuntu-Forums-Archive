---
title: "Mouse Cursor Wrapping Screen Error"
date: 2008-02-14
forum: General Help
---

### Post by srankin1826 on 2008-02-14
I am using two 1280x1024 monitors connected to the VGA port on my thinkpad T61 via a Matrox DualHead2Go analog edition.  This neat little box makes it appear to the T61 that instead of having 2 monitors attached, I have a single 2560x1024 monitor attached.

Some xorg.conf configuration was necessary to get it to boot into X properly (proper Modeline added).  xrandr appears to work fine.

The problem is that when the mouse cursor goes beyond 2048 on the right of the screen, it wraps to the left of the screen.  This is quite weird in that while the cursor appears to be wrapped onto the left side of the screen, it is functionally still on the right side of the screen.

Example:  The log-off button is on the upper right corner of my dual display.  When I move the cursor to the upper right of the screen, it visually appears to be near the middle of the left display, but when I click the left button, it brings up the log-off dialog.  

Can anyone offer any suggestions?

thanks,

Sam

---

### Post by srankin1826 on 2008-02-15
Quick update:

I've tried booting from a xubuntu live cd.  Problem persists.  I've tried enlightenment desktop manager.  Problem persists.

Any help is much appreciated.  This is the one thing keeping me from going 100% linux.

thanks in advance,

Sam

---

### Post by srankin1826 on 2008-02-15
One more update:

I removed the dualhead2go.  With the ModeLine still in my xorg.conf I was able to output 2560x1024 to my single 1280x1024 display.  The issue still exists.  So this isn't a matrox dualhead2go hardware issue.  It is something to do with linux/xorg/gnome/???

--Sam

---

### Post by fatespeaks on 2008-02-29
I think I have seen behavior like this before.  But, I am pretty sure it was before I was using TripleHead2Go.  Might this be something with HW_Cursor vs SW_Cursor?

Per your request, here is my xorg.conf, though I am not sure it will help:
```
# xorg.conf (xorg X Window System server configuration file)

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
    	Identifier     	"HP USB Mouse"
    	Driver         	"evdev"
    	Option         	"Name" 		"Logitech Optical USB Mouse"
EndSection

Section "InputDevice"
	Identifier  	"kensington"
	Driver      	"evdev"
    	Option		"Name" 		"ThinkPS/2 Kensington ThinkingMouse"
	Option		"Buttons"	"5"
      	Option      	"ButtonMapping" "3 6 1 7 2"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"		"True"
	Option		"AddARGBGLXVisuals"		"True"
	Option		"NoLogo"			"True"
#	Option		"DisableGLXRootClipping"	"true"
EndSection

Section "Modes"
	Identifier	"Modes[0]"
	# V-freq: 60.00 Hz  // h-freq: 63.73 KHz
	Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062 
	# V-freq: 60.00 Hz  // h-freq: 63.42 KHz
	Modeline "3840x1024" 301.37  3840 3920 4224 4752 1024 1027 1030 1057
EndSection

Section "Monitor"
	Identifier	"TripleHead2Go"
	VendorName	"Matrox"
	ModelName	"3840x1024@60Z"
	Option		"DPMS"
	Option		"UseEDIDFreqs"		"false"
	Option		"UseEdidDpi"		"FALSE"
	Option		"DPI"			"96 x 96"
	UseModes	"Modes[0]"
	Horizsync	28-64
	Vertrefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"TripleHead2Go"
	Defaultdepth	24
	SubSection "Display"
		Modes	"3840x1024"	"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"Default Screen"
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
#	Inputdevice	"Configured Mouse"	"CorePointer"
	InputDevice	"HP USB Mouse"		"CorePointer"
	InputDevice	"kensington"		"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection
```
Cheers,
Aaron Ahlemeyer

---

### Post by srankin1826 on 2008-03-04
Thanks fatespeaks!!!

This worked:

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "HW_cursor"     "off"
        Option          "SW_cursor"     "on"
EndSection


Have you figured out how to "split" the screens so that a maximize doesn't take up both (all three in your case) monitors?

thanks,

Sam

---

### Post by fatespeaks on 2008-03-08
Yes, now I remember.  I saw the weird cursor issue that you described when I was testing the integrated Intel graphics on my system with triplehead2go.  I am glad that SW_cursor solved the issue.  BTW, I think having both HW_cursor off and SW_cursor on options is redundant.  But, I doubt it will cause any harm.

Using a fake-Xinerama option in the NVidia driver I was able to split the screens.  But it seems to cause other problems.

On another note, make sure you keep a backup of your xorg.conf in case an upgrade of xorg or drivers overwrites it.

Cheers,
Aaron

---

