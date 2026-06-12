---
title: "Double click on desktop kills X server. WHAT THE HELL?"
date: 2008-03-03
forum: General Help
---

### Post by mental_gnome on 2008-03-03
So i've just propertly setup ATI video card drivers.
Second monitor is working propertly too.
Now i have like two desktops with panels icons and stuff.
Everything's kinda working happily.

**Now when I double click on the first desktop(not sure if it's primary or not), X server gets killed and restarted.**

**Effect equal to that of Ctrl+Alt+Backspace!**

HUH?

NOTE: this only works on first desktop, not both! I can click and move icons around on second desktop as much as i want.

I've no idea why this is happening. 
Is there some logs I might look into to find out what's going on?

Could it be related to xorg.conf mouse part(i tried to make all 4 Intelli Explorer buttons to work - failed though). If so, then why this happens only on one of the screens?

HELP! THIS IS CRAZINESS!

---

### Post by mental_gnome on 2008-03-03
Found this in syslog:
gdm[16471]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

Not very verbose.

Basically, it's not even a double click. I can click on a icon once. Then click on an empty space anywhere(to lose focus from icon) and it restarts too.

---

### Post by mental_gnome on 2008-03-03
**Found a workaround:**
Disabled visual effects in System > Preferences > Appearance from Normal to None.

:?

---

