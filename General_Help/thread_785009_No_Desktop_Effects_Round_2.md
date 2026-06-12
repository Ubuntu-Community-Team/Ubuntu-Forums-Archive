---
title: "No Desktop Effects: Round 2"
date: 2008-05-07
forum: General Help
---

### Post by CarnivorouZ on 2008-05-07
If anyone wants to take another stab at this problem, I am open to any suggestions.  If I install my ATI driver for my Radeon x1650 card I will end up with a black screen immediately after the splash screen.  
Here is what my xorg currently looks like:
```
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
	Option        	"VideoOverlay"    "on"
    	Option        	"OpenGLOverlay"    "off"
    	Option        	"XaaNoOffscreenPixmaps"    "true"
    	Option        	"AddARGBGLXVisuals"    "true"
    	Option        	"AllowGLXWithComposite"    "true"
    	Option        	"EnablePageFlip"    "true"
    	Option        	"AccelMethod"         "EXA"
    	Option        	"MigrationHeuristic"     "greedy"
    	Option        	"DRI"            "true"
    	Option        	"TexturedVideo"        "on"
    	Option        	"UseFastTLS"        "0"
    	Option        	"BlockSignalsOnLock"    "on"
    	Option        	"KernelModuleParm"    "locked-userpages=0"
    	Option        	"ForceGenericCPU"    "off"
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

Section "Extensions"
    Option        "Composite"    "1"
EndSection

Section "ServerFlags"
    Option        "AIGLX"    "true"
EndSection

Section "DRI"
    Mode    0666
EndSection
```
Thanks for any help anyone can offer, if nothing works then I will just wait and hope MOTU comes up with an update that fixes this problem. Thanks guys.

---

### Post by katomic on 2008-05-07
I've got a hp laptop with the ATI Mobility Radeon X1600 (256 MB)
.
Had major display performance issues, also desktop effects would fail without error msg. Fixed it by installing the linux ati driver & control panel. google forit.

---

