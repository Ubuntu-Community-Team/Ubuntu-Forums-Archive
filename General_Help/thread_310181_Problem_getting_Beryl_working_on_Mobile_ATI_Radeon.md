---
title: "Problem getting Beryl working on Mobile ATI Radeon."
date: 2006-11-30
forum: General Help
---

### Post by jeremyrain on 2006-11-30
I've gone through just about every howto there is for getting Beryl working with an ATI/Radeon card. It still wont take over as the window manager.

When I run beryl-manager in a terminal, I see this every time:

> extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Now, when it finishes loading itself, and I try to select "beryl" as the window manager from the little gem icon, the rest of this appears:

> XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

The bizarre thing is glx is being loaded per my xorg.conf file. I can't figure it out. Is there anything I can check that might show me where the problem is?
](*,)

---

### Post by igknighted on 2006-11-30
can you please post your xorg.conf, and the output of 'glxinfo | grep direct'

---

### Post by jeremyrain on 2006-11-30
Here you go:

> # glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

and the relevant sections:

> 
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
	Load	"GLcore"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver		"radeon"
	BusID		"PCI:1:5:0"
	Option		"BusType" "PCI"
	Option		"AGPMode" "4"
	Option		"AGPSize" "32" # default: 8
	Option		"AGPFastWrite" "false" # More stable this way.
	Option		"SWcursor" "true" # More stable this way.
	Option		"EnablePageFlip" "true" # Faster.
	Option		"EnableDepthMoves" "false" # More stable this way.
	Option		"RenderAccel" "false" # More stable this way
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable
	Option		"DDCMode"
	Option		"SubPixelOrder" "NONE"
	Option		"ColorTiling" "false" # More stable this way.
	Option		"DynamicClocks" "true"
	Option		"bioshotkeys"   "True"
	Option		"XAANoOffscreenPixmaps" "true" # More stable this way.
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
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


---

### Post by jeremyrain on 2006-11-30
I also neglected to mention that I'm running edgy.

---

### Post by jeremyrain on 2006-12-01
Disregard this thread.... I managed to correct my error.

I reinstalled the ATI Radeon driver, updated, tweaked a few other things and glx and beryl are now working.

---

