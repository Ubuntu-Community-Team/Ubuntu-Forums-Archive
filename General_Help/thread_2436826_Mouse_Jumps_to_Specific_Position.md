---
title: "Mouse Jumps to Specific Position"
date: 2020-02-13
forum: General Help
---

### Post by Uruz on 2020-02-13
I have two monitors. A few hours ago, my mouse started jumping to a specific position right on the edge where they meet, this happens randomly, and may not happen for 10+ seconds, or it may happen multiple times in one second. I think it's more likely to happen when the mouse is moving. xdotools gives the coordinates as (1359, 694) on screen 0 (interestingly, xdotools always reports "screen: 0" regardless of which monitor the mouse is on. I don't know if this is new or not). I can't tell if the mouse is moving to this position, or if it's "crashing" and being reset to this position. If I'm clicking something when it happens, it drags whatever I'm trying to click.

Rebooting didn't help, and I can't find reports of this anywhere. It started randomly without me installing or changing anything beforehand. It happens regardless of whether or not I have a mouse plugged in. I've looked to see if there are error logs that would be created by the pointer service crashing, but I didn't find anyone mentioning them anywhere.

Anyone know what might be the issue or have an idea of how to diagnose a problem like this?

EDIT:
Forgot to mention. If I only have one monitor, it still happens, although the coordinates are (0, 694) because the second monitor isn't there for it to cross onto.

EDIT 2:
Turns out it was my pen getting placed too close to my drawing tablet when I re-arranged some stuff. Ignore me, I'm an idiot.

---

### Post by TheFu on 2020-02-13
Check for a BIOS update. 
Also, completely removing power, including any battery (laptop and mouse), for a few minutes, has been known to help.
To rule out the mouse hardware, unplug it and try a different pointing device. Sometimes failing hardware begins by emitting extra events or missing events.  This applies to keyboards too.

I really hope you aren't on 15.10 still.

---

