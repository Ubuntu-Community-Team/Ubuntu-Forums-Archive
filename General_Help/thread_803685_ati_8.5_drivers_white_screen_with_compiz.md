---
title: "ati 8.5 drivers white screen with compiz"
date: 2008-05-22
forum: General Help
---

### Post by milanvora2 on 2008-05-22
just installed at 8.5 drivers and i get the a white screen if i use compiz.
If i disable compiz then everythign works
Any idea how to fix this.

---

### Post by dreamcruiser on 2008-05-24
i have the same problem with ati 8.5 driver. Perhaps same lines in /etc/X11/xorg.conf will help, i will try it...

---

### Post by Forlong on 2008-05-24
Post the output of ```
grep -v ^# /etc/X11/xorg.conf
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by milanvora2 on 2008-05-24
i re-installed older drivers with envy and then overwrote the drivers with the new ones and the problem was solved.

Here is my xorg.conf:

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "AccelMethod" "EXA"
	Option	    "MigrationHeuristic" "greedy"
	Option	    "DRI" "true"
	Option      "RenderAccel" "True"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
        Option      "TexturedVideo" "off"	
	Option	    "UseFastTLS" "1"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "KernelModuleParm" "locked-userpages=0"
	Option	    "ForceGenericCPU" "off"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "Textured2D" "on"
	Option	    "TexturedXrender" "on"
	Option	    "BackingStore" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
#	Option	    "RENDER" "Enable"
#	Option	    "DAMAGE" "Enable"
#	Option	    "Composite" "Enable"
EndSection

---

