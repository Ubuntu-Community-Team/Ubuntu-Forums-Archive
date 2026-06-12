---
title: "[SOLVED] Mouse Button Setup for Firefox"
date: 2007-10-07
forum: General Help
---

### Post by fjgaude on 2007-10-07
Has anyone successfully gotten a modern wheel mouse with back, forward buttons to work with Firefox browser? I've tried and tried using xev to determine the mouse button numbers, xmodmap -e "pointer = 1 2 3 4 5 6 7" to set the numbers, and xorg.conf to map, all without success, using a seven botton mouse.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
        Option          "Buttons"       "7"
	Option		"ZAxisMapping"	"4 5"
#	Option		"ZAxisMapping"	"6 7"
#	Option		"Emulate3Buttons"	"false"
EndSection
```

Firefox is hard wired to 4 and 5 for back and forward.

---

### Post by fjgaude on 2007-10-08
Here's all it took for a Microsoft seven button, wheel optical mouse to fully work with Firefox, change /etc/X11 xorg.conf file to:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device"                "/dev/input/mice"
        Option      "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"       "false"
        Option      "Buttons"               "7"
        Option      "ZAxisMapping"          "4 5"
        Option      "ButtonMapping"         "1 2 3 6 7 4 5"
EndSection
```

Hope this helps others.

---

### Post by dotCOM41799 on 2007-10-12
How do you change the speed that you scroll with the wheel mouse?

---

### Post by BLTicklemonster on 2007-10-12
Or you coulda done this:

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by BoardDWorld on 2007-10-22
> **fjgaude said:**
> Here's all it took for a Microsoft seven button, wheel optical mouse to fully work with Firefox, change /etc/X11 xorg.conf file to:

```
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device"                "/dev/input/mice"
        Option      "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"       "false"
        Option      "Buttons"               "7"
        Option      "ZAxisMapping"          "4 5"
        Option      "ButtonMapping"         "1 2 3 6 7 4 5"
EndSection
```

Hope this helps others.

It certainly did, works like a charm! Thanks very much. :)

---

