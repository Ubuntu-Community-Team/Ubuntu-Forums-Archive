---
title: "complete noob, need instruction/walkthrough on writing a simple script."
date: 2021-07-10
forum: General Help
---

### Post by penciltester on 2021-07-10
Hi folks, I'm needing instruction on writing a script to run at start up. As of now i'm having to open terminal and enter these commands after each reboot. 

DEVICE="Tablet Monitor Pad pad"
xsetwacom set "$DEVICE" Button 1 0
xsetwacom set "$DEVICE" Button 2 0
xsetwacom set "$DEVICE" Button 3 0
xsetwacom set "$DEVICE" Button 4 0
xsetwacom set "$DEVICE" Button 5 0
xsetwacom set "$DEVICE" Button 6 0
xsetwacom set "$DEVICE" Button 7 0
xsetwacom set "$DEVICE" Button 8 0
xsetwacom set "$DEVICE" Button 9 0
xsetwacom set "$DEVICE" Button 10 0

and then run a python script

[FONT=monospace][COLOR=#000000]python3 huion_keys.py

[/COLOR]How would I go about writing a script to accomplish this at start up? Thanks in advance for the instruction/help.

[/FONT]

---

### Post by TheFu on 2021-07-11
Create a file with this inside:
```
$!/bin/bash
DEVICE="Tablet Monitor Pad pad"
xsetwacom set "$DEVICE" Button 1 0
xsetwacom set "$DEVICE" Button 2 0
xsetwacom set "$DEVICE" Button 3 0
xsetwacom set "$DEVICE" Button 4 0
xsetwacom set "$DEVICE" Button 5 0
xsetwacom set "$DEVICE" Button 6 0
xsetwacom set "$DEVICE" Button 7 0
xsetwacom set "$DEVICE" Button 8 0
xsetwacom set "$DEVICE" Button 9 0
xsetwacom set "$DEVICE" Button 10 0
python3 /full/path/to/huion_keys.py
```
After creating the file, run **chmod +x /path/to/new/file** so it is executable.  If it were me, I'd put the file in $HOME/bin/ and name is something like "tablet-init".  So **nano ~/bin/tablet-init** is one possible the edit command and the **chmod +x ~/bin/tablet-init** . Simple.  If ~/bin/ doesn't exist, create the directory.  Put all your scripts into there.

Next, tell the auto-run in your GUI to use that file.  Each different DE uses a different autorun at session startup method.  The "Ubuntu Desktop Guide" explains it for Gnome3, but LXQt, KDE, Mate, and others will use different methods.  I know that openbox looks for an autorun file in ~/.config/openbox/.  That probably doesn't apply to 95% of the people reading this.

BTW, you probably want to change **xsetwacom** to be the full path to that program and not trust your PATH environment variable. Not the end of the world, but there could be problems in the future.

---

### Post by penciltester on 2021-07-11
Lol figured out my issue on this not seeming to work properly. First thank you for showing the example script. It gave me an understanding of how to structure a simple bash script. It wasn't as complicated as I thought it was going to be. One edit though '$!/bin/bash' didnt work. I edited it to '#!/bin/bash' and things worked swimmingly. Thanks again!

---

### Post by TheFu on 2021-07-11
Forum reply issues problems. Reply is here:http:// s p r u n g e . u s /ji7oTB
I haven't a clue why.

---

