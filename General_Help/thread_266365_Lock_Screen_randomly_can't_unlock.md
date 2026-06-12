---
title: "Lock Screen randomly can't unlock"
date: 2006-09-27
forum: General Help
---

### Post by Pichu0102 on 2006-09-27
For over a month, I've had this problem on my Presario laptop, when I close the screen, and open it back up, it doesn't respond to keypresses or the mouse, and won't show the unlock dialog, leaving me having to hard shutoff the computer and turn it back on.
What could be wrong?

---

### Post by yopnono on 2006-09-27
Try to add this to the /etc/X11/xorg.conf in the (section "Device")

```
Option          "VBERestore"		"true"
```


Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
        *Option          "VBERestore"		"true"*
EndSection

---

### Post by Pichu0102 on 2006-09-28
> **yopnono said:**
> Try to add this to the /etc/X11/xorg.conf in the (section "Device")

```
Option          "VBERestore"		"true"
```


Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
        *Option          "VBERestore"		"true"*
EndSection

That didn't work... But these are the lines that were in there before, however...

	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"

---

