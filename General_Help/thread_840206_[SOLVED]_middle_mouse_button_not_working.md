---
title: "[SOLVED] middle mouse button not working"
date: 2008-06-25
forum: General Help
---

### Post by dexter.deepak on 2008-06-25
on gutsy i used it frequently for copy-paste, but on hardy it aint working !!
is it a flaw in my system..or sth. new in hardy ?

i think "dpkg-reconfigure xserver-xorg" can help me..but i am afraid of using it , it always introduces a new problem whenever i play with it.

cant i simply edit /etc/X11/xorg.conf to tackle the problem ? afterall it is the config file of xserver ..

---

### Post by erginemr on 2008-06-25
It would help if you could post the contents of "/etc/X11/xorg.conf", which we can then compare with ours.

---

### Post by dexter.deepak on 2008-06-25
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
```

---

### Post by dexter.deepak on 2008-06-25
i just "had" to try dpkg-reconfigure xserver-xorg
...but i am not even getting the option to edit the mouse settings !!
i am just having the options to adjust the keyboard layout...not even the screen-resolution...

i smell some big change from gutsy to hardy...

---

### Post by erginemr on 2008-06-26
Your xorg.conf file is almost the same as mine. I guess you will have to look elsewhere (any custom keyboard/mouse shortcut settings in "Compiz -ccsm" or "Keyboard Shortcuts" for that matter):
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
EndSection
```

And here is the one that existed back in Gutsy:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

You may consider trying these, followed by a Ctrl+Alt+BackSpace...

---

### Post by cariboo on 2008-06-26
This is my mouse section in xorg.conf on Intrepid:

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

So if this works on a pre-alpha release it should work in hardy. I see erginemr has the same in Gutsy

I'd suggest change it to this and the previuos and see what happens, remember to back up xorg.conf first.

Jim

---

### Post by dexter.deepak on 2008-06-26
i tried only the emulate3buutons options..but it aint working.

one thing i'd like to know...doesnt reconfiguring X11 want a restart ?
erginemr said that just logging out would do...i thought xserver restarts only on system restart !

---

### Post by erginemr on 2008-06-26
I am sorry that it didn't work? Did you check the Compiz shortcuts? Another way to learn is to temporarily disable Compiz:
```
Alt+F2 >> metacity --replace
```
Does the middle mouse button work now?

To re-enable it:
```
Alt+F2 >> compiz --replace
```

Redarding your question on X:
```
Ctrl+Alt+BackSpace
```
resets the X server, and in some cases
from a virtual terminal with Ctrl+Alt+F1-6;
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```
restarts the gdm login manager.

---

### Post by erginemr on 2008-06-26
This is very strange, because middle-button pasting is the standard, omnipresent behavior in all Unix-like systems. 

If we turn our attention to the hardware, the middle button of your mouse might as well be broken. To check this, try Firefox, under tools >> settings >> advanced >> enable automatic scroll (or something of that kind, as I am not using Firefox in English). Now open a web page and try your middle-button to check if it functions.

---

### Post by dexter.deepak on 2008-06-26
thanks for all the support..
i dont know why, but on my second (and not the first) restart , it started working..thanks a lot.

---

