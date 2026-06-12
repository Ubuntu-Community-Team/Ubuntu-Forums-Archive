---
title: "Imwheel no longer works with Edgy?"
date: 2006-11-01
forum: General Help
---

### Post by glennric on 2006-11-01
I have been using imwheel in combination with xbindkeys to get the side buttons on my mouse to do certain things that I want them to do.  I upgraded to Edgy and now imwheel complains that there are unrecognized actions in the imwheelrc config file.  I haven't changed anything in that file, and imwheel shouldn't have changed either.  I know the side buttons on my mouse are recognized, as now I get the stupid forward and back page in Firefox.  Does anyone know how to get imwheel to work the way it should?

---

### Post by Aldrik on 2006-11-05
I had the exactly the same problem, I managed to fix it by changing my config to use **Left** & **Right** (Thumb1, Thumb2, Button4/5/6/7 don't seem to work any more). Then I needed to change the button grabbing **imwheel -k -b "8 9 6 7"** & all works fine now.

---

### Post by glennric on 2006-11-06
Thanks, I managed to figure it out.  I had been using Up and Down, now I need Right and Left.  Also I was able to use `imwheel -k` with no button specification.

---

### Post by Aldrik on 2006-11-07
> **glennric said:**
> Thanks, I managed to figure it out.  I had been using Up and Down, now I need Right and Left.  Also I was able to use `imwheel -k` with no button specification.Good to hear, the problem with not specifying button grabbing is (then imwheel controlls the wheel and) key plus wheel shortcuts don't work (like shift+wheel to zoom in GIMP). ;)

---

### Post by zeltak on 2006-11-17
hi

Can anyone post their xorg.conf and imwheelrc files? i am having major problems with this..

thx alot

Zeltak

---

### Post by mgmiller on 2006-11-18
Here is my xorg.conf file.  My buttons work fine in Firefox 2.0 with it.
```

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" 		"/dev/input/mice"
        Option      "Protocol" 		"ExplorerPS/2"
        Option      "ZAxisMapping" 	"6 7"
        Option      "ButtonMapping" 	"1 2 3 4 5"
EndSection
```

I have not been able to get imwheel to get my side buttons working in nautilus with Edgy yet though.

---

### Post by jpaddison83 on 2006-11-23
I think I've tried about 50 different configurations of xorg.conf, imwheelrc and my startup script, but this is what has finally got my MX510 working on Edgy. Hope it helps...

-- /etc/X11/xorg.conf --
[B]Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"[/B]
EndSection

--/home/login/mouse-- (my startup script)
[B]#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7" &
exec imwheel -k -b "6 7 8 9" &
exec $REALSTARTUP[/B]

--/etc/X11/imwheel/imwheelrc-- (default with the following appended at the end)
[B]".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right 

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right[/B]

---

### Post by jeremy on 2006-11-29
I have a M$ intellimouse explorer, and using Kubuntu edgy I did:

sudo kate /etc/X11/xorg.conf

and replaced the 'mouse section with:
Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ZAxisMapping" "4 5"
        Option "ButtonMapping" "1 2 3 6 7" 
        Option "Resolution" "100"
EndSection

Then installed imwheel from the repos, then created a file in the home dir called 
.imwheelrc

containing:

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

then made a file called 'mouse' (executable file in ~/.kde/Autostart)
containing:

#!/bin/bash
killall imwheel
xmodmap -e "pointer = 1 2 3 4 5 6 7"
BINARY=$(which imwheel)
$BINARY -k -p -b "67"

Then restarted Edgy and can now use the left (back) and right (forward) buttons as well as the scroll wheel in firefox AND konqueror.

---

### Post by tweak on 2007-01-27
> **Aldrik said:**
> I had the exactly the same problem, I managed to fix it by changing my config to use **Left** & **Right** (Thumb1, Thumb2, Button4/5/6/7 don't seem to work any more). Then I needed to change the button grabbing **imwheel -k -b "8 9 6 7"** & all works fine now.

Are you able to explain exactly what you changed? I can't seem to get imwheel working correctly for my intellimouse either :(.

The contents of my /etc/X11/xorg.conf:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "false"
    Option        "Buttons"        "7"
    Option        "ZAxisMapping"        "4 5"
    Option        "ButtonMapping"        "1 2 3 6 7"
    Option        "Resolution"        "100"
EndSection
```/etc/X11/imwheel/imwheelrc:
```
".*"
None, Up, Control_L|V
None, Down, Control_L|C
``` (I want copy and paste on my buttons, not forward/back). There is a bunch of crap for other applications as well which I'm not sure if I'm supposed to delete or keep - thoughts?

~/.imwheel.sh:
```
#/bin/bash
imwheel -b67
```I'm at a loss as to what's bad about these so any help on the issue would be fantastic.

---

