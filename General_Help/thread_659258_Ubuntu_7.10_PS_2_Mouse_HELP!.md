---
title: "Ubuntu 7.10 P/S 2 Mouse HELP!"
date: 2008-01-05
forum: General Help
---

### Post by niqqq on 2008-01-05
my PS/2 mouse does not move in ubuntu. (yes it does in windows Xp)

this problem started ever since the LIVE CD, but i still managed to install it using my keyboard (alt-shift-numlock).

now everything is fine in my newly installed Gutsy Gibbon EXCEPT FOR THE MOUSE!

please help me!

---

### Post by geraldm on 2008-01-05
Make sure the mouse cable is plugged into the PS/2 port correctly.  It should show up in the log
```

dmesg | grep "mouse" -

```
You should see a line like:
mice: PS/2 mouse device common for all mice

You might check for a simple change first.  What protocol is specified in file /etc/X11/xorg.conf

A PS/2 mouse might have a protocol line like:
  Option    "Protocol"    "ImPS/2"

If that line  is not found, you might backup that file, then make the change to the protocol line,
and restart X; otherwise post the "Section Input Device" for the mouse.

Gerald

---

### Post by niqqq on 2008-01-05
i have tried that but to no avail...

anyway, i found a solution.

googled it and another one having the same problem replaced his PS/2 mouse with a USB one.

worked for me too..

it is still weird why ubuntu doesn't work with the PS/2 one's.


anyway, who cares.. i can use Linux now. And it rocks.

---

