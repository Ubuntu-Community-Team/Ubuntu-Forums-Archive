---
title: "Does compiz works with my system??"
date: 2008-05-03
forum: General Help
---

### Post by shokoup on 2008-05-03
Hello, i'm using kubuntu, kde4, i tried to change any compiz setting or changing any default settings related to the desktop or appearance, but nothing happened.
i'm using 1.8 Ghz processor, 768 MB Ram, builtin 32 MB S3 prosavage Card
i opened the hardware drivers see my VGA card, i found "no proprietary card installed on this system.
if my builtin card doesn't support, could u please tell me a brand tested and works with my old machine?  i have VGA slot to put another card.

bye:guitar:

---

### Post by vishzilla on 2008-05-03
In the terminal enter ```
glxinfo | grep render
``` post the output here

---

### Post by shokoup on 2008-05-05
Thanx for your help, here is the output:

direct rendering: Yes
OpenGL renderer string: Mesa DRI ProSavageDDR 20061110 AGP 1x x86/MMX/SSE2

---

### Post by shokoup on 2008-05-21
any help ??  :( i removed Kde 4 and installed kubuntu and installed the stable version 3.5.9, the Compiz engine is installed, when i choose any effect, nothing happen!!

---

### Post by Forlong on 2008-05-22
Run this to see where it fails: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by shokoup on 2008-08-30
> **Forlong said:**
> Run this to see where it fails: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Thanx for helping, i changed KDE4 because of lot of bugs, as i read, so i returned to version 3.5.9 this is the output:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         S3 Inc. VT8375 [ProSavage8 KM266/KL266]
 Driver in use:         savage
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checkin for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on the whitelist.


```

---

