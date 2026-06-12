---
title: "Cut and Paste buttons on MS Trackball Optical"
date: 2008-05-03
forum: General Help
---

### Post by radagast89 on 2008-05-03
I have spent a LONG time trying to configure the extra buttons on my trackball.  I finally got them working the way they're meant to out of the box (forward and backward in the browser).  I can't for the life of me figure out how to change their function, however.  I want them to be Cut and Paste.  Also, I'd like clicking the wheel to be Enter.  I've been using this device this way in Windows for years, and it's driving me nuts.

My imwheelrc looks like this...

```
".*"
None, Up, Control_L|X
None, Down, Control_L|V
```

imwheel startup.conf looks like this...

```
IMWHEEL_START=1

IMWHEEL_PARAMS='-b "6 7"'
```

xorg.conf's mouse section looks like this...

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Buttons"       "7"
	Option		"ButtonMapping"	"1 2 3 6 7"
        Option          "ZAxisMapping"  "4 5"
	Option		"Resolution"	"100"
        Option          "Emulate3Buttons"       "false"
EndSection
```

Xmodmap looks like this...
```

! Re-order the mouse buttons
pointer = 1 2 3 4 5 6 7
```

Anyone have any idea what I'm doing wrong?  From everything I've seen, the cut and paste should be working.  I have NO idea how to change the function of the wheel click.

---

