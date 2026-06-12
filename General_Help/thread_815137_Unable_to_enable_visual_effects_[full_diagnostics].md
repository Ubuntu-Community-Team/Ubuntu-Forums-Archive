---
title: "Unable to enable visual effects [full diagnostics]"
date: 2008-06-01
forum: General Help
---

### Post by user402 on 2008-06-01
I am unable to enable visual effects - anything other than "none" is not allowed. Here is some information on my system:

MSI P4M900M3 S775
Intel Core 2 Duo E4600, 2.40 Ghz, 2MB L2 Cache, 800 MHz FSB
VIA P4M900 Chipset based
1GB DDR667 RAM

The retailer stated "32MB graphics". Here is the ad for the system on their website:
[http://www.chaosnet.co.za/index.php?id=2319](http://www.chaosnet.co.za/index.php?id=2319)

I installed Ubuntu 8.04, but had trouble - after the initial loading screen, the display on the screen was barely readable. I was not being displayed properly. This is at the point where you configure the computer. I tried again, but still the same problem came up. Completely disfigured display. I then installed in "graphics safe mode" which worked. But now I am unable to enable any visual effects.

Here is some output from the terminal:

1. When I ran "compiz --replace":
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity


2. I tried "glxgears" in the terminal and I COULD see the 3 gear turning smoothly. Here was the output from the first couple of seconds:
4998 frames in 5.0 seconds = 998.114 FPS
5020 frames in 5.0 seconds = 1000.513 FPS
5020 frames in 5.0 seconds = 1001.649 FPS


3. Here is the output from "_":
_________________________________________________
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
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
_________________________________________________


4. Here is the output from the "./compiz-check" (part of the compiz check):
____________________________________________________________________
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Detected driver is not on Compiz' whitelist. 
____________________________________________________________________

Any suggestions?

Thanks

---

### Post by klange on 2008-06-01
You have a VIA graphics chipset, which isn't going to work, and regardless, you're using the VESA drivers, which don't do hardware 3d. Supposedly, there will be work done on the VIA drivers (by VIA themselves) to improve 3d support, and hopefully may lead to the supported OpenGL extensions Compiz needs to run.

---

### Post by Forlong on 2008-06-01
Here's a guy who claims he got it working on a VIA chip: [http://ubuntuforums.org/showthread.php?p=5040406#post5040406](http://ubuntuforums.org/showthread.php?p=5040406#post5040406)
You might wanna give that a try.

---

