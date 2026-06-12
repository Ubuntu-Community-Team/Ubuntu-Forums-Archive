---
title: "Middle mouse button question"
date: 2007-01-28
forum: General Help
---

### Post by raul_ on 2007-01-28
I've searched the forums but i haven't been able to find a solution. The problem normally is mapping. My mouse works fine. But my middle mouse button acts the same way number 4 does. I know this because i use xbindkeys to give 4 button a double-click behaviour, and that's what my middle button does. 

Here's xorg.conf
```

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "false"
	Option	    "Buttons" "7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "ButtonMapping" "1 2 3 6 7"

```

Any ideas on this? I'm asking this because i would like to use the middle click feature in Epiphany (that opens a link in a new tab)

---

### Post by raul_ on 2007-01-29
Bad timing to post :P just to get this back in the list

---

### Post by fragos on 2007-01-29
Some applications configure the middle button for their use as for paste or enhanced scrooling.  Open office does this in the Tools-> Options-> Openoffice.org-> View.  There may be others in the Configuration Editor.

---

### Post by raul_ on 2007-01-30
ok I got it. Just changed to "ExplorerPS/2" in my xorg.cong and then corrected the xbindkeys conf file :)

---

