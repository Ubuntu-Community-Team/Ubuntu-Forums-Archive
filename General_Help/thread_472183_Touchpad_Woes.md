---
title: "Touchpad Woes"
date: 2007-06-12
forum: General Help
---

### Post by RelativelyQuantum on 2007-06-12
I'm having some serious trouble with my xorg.conf file; i.e., it's completely non-responsive. My synaptics touch pad has reverted to its default settings, and it takes three swipes to move the cursor across the screen. Here are my xorg settings, which worked until now:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"MaxTapTime"		"0"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option          "MinSpeed"              "0.60"
	Option          "MaxSpeed"              "1.60"
	Option          "Accelfactor"           "0.030"
	Option          "EdgeMotionMinSpeed"    "200"
	Option          "EdgeMotionMaxSpeed"    "200"
EndSection
```

Any help would be greatly appreciated.

---

### Post by RelativelyQuantum on 2007-06-12
At this point anything would help. Should I move the file to a different folder?

---

