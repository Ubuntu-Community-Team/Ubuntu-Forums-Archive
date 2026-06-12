---
title: "Mouse randomly disappearing?"
date: 2007-07-08
forum: General Help
---

### Post by ARandomKid on 2007-07-08
I recently had to reinstall Linux and am currently using Knoppix (Kubuntu? ;o_o Maybe that's what that stands for...but anyways, I'm just using it waiting for the CD (7.04) I recently ordered to arrive. 6-10 weeks to go! :P This works perfectly fine, however...), but had a similar problem with Ubuntu as well.

The mouse, on occasion, seems to disappear at complete random. No cursor, and I can't do anything with the mouse itself, only the keyboard works.

This usually doesn't happen unless I leave the computer alone for a while (generally about 2 hours or so, though I've had it happen sooner than that)...

...and I'm clueless as to how I can resolve this. Not that it's a major problem, just REALLY annoying having to unplug my computer's power source and wait 5 minutes for it to shut down, then go through the whole boot process every time. (Which is the only reason I LIKE having a horrible battery in this laptop! Makes this a LOT less painful.)

---

### Post by geraldm on 2007-07-08
This may be of some help:
in file /etc/X11/xorg.conf for the mouse driver, make sure the 
option for the mouse device is 
 "Device" "/dev/input/mice"
avoid "/dev/input/mouse0"
This allows all mice (even if there is only one) to use the cursor.

There was a problem for SOME recent computers with power management
suspending the usb subsystem.  After suspension, the usb devices would not 
work until the suspension is lifted.  This problem can be solved by not selecting
the power conservation options until that bug is fixed.

Gerald

---

### Post by ARandomKid on 2007-07-08
> **geraldm said:**
> This may be of some help:
in file /etc/X11/xorg.conf for the mouse driver, make sure the 
option for the mouse device is 
 "Device" "/dev/input/mice"
avoid "/dev/input/mouse0"
This allows all mice (even if there is only one) to use the cursor.

There was a problem for SOME recent computers with power management
suspending the usb subsystem.  After suspension, the usb devices would not 
work until the suspension is lifted.  This problem can be solved by not selecting
the power conservation options until that bug is fixed.

Gerald

The file doesn't exist - I even did a search for "xorg" to be certain. :(

---

