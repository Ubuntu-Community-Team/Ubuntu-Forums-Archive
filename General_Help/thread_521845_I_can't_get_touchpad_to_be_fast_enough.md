---
title: "I can't get touchpad to be fast enough"
date: 2007-08-09
forum: General Help
---

### Post by Ryzol on 2007-08-09
The relevant portion of my xorg.conf is:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option 		"SHMConfig"
	Option 		"MinSpeed"		"1.0"
	Option		"MaxSeed"		"9999999.0"
	Option		"AccelFactor"		"999.0"
EndSection
```

I tried using more sane numbers but couldn't notice a difference so I jacked them way up and I still can't tell if it is faster. This really annoys me because I want to be able to flick my finger and send my mouse from one end of the screen to another on a 1280x800 res screen. Right now it doesn't even get halfway. :(

---

### Post by 5-HT on 2007-08-10
Are you restarting X after making the changes? I'd try setting SHMconfig on in your xorg.conf and using synclient to adjust and monitor the settings on the fly. Do the settings take effect then? If so, you can edit xorg.conf accordingly. 
```
 Option         "SHMConfig"        "on"
```Here's what I'm using
```
Option        "MinSpeed"        "0.8" 
Option        "MaxSpeed"        "1.4" 
Option        "AccelFactor"        "0.1" 
```

---

### Post by Ryzol on 2007-08-11
Changed it to on, ctrl+alt+backspace restarts X, right? Tried "synclient -m 100" and got this error message: "Can't access shared memory area. SHMConfig disabled?"

---

### Post by 5-HT on 2007-08-11
> **Ryzol said:**
> Changed it to on, ctrl+alt+backspace restarts X, right? Yup. Could try a full reboot, but there should be no need.
I'm kinda stumped...as long as the syntax is correct in you xorg.conf, you should be able to monitor touchpad events and change settings with synclient. Are you using a Synaptics/Alps touchpad and the synaptics driver is installed? I wonder what happens if you install gsynaptics (gtk, GUI touchpad config application. There's a KDE-lib version available too) and try to change touchpad settings from there?

---

### Post by Ryzol on 2007-08-11
Installed gsynaptics tried to run it and got this error message: "GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics". So I edited /etc/X11/xorg.conf and changed it from on to true. Saved, restarted X, tried to run gsynaptics and got the exact same error message. :confused:

I'm attaching my xorg.conf in the hopes it will be useful.

---

