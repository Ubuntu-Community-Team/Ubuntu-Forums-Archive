---
title: "Mouse Cursor Constantly Flickering/Disappearing"
date: 2018-10-11
forum: General Help
---

### Post by antisthenes2 on 2018-10-11
After enabling the software cursor in order for redshift to also affect the colour temperature of my mouse cursor, which it did, my cursor is now constantly flickering and at times disappearing, as well as moving on its own.

I enabled the software cursor by creating a .conf file with this:

```
Section "Device"
Identifier "Nvidia 9400"
Driver "nouveau"
Option "SWCursor" "true"
EndSection
```

and placing it in /etc/X11/xorg.conf.d.

---

### Post by TheFu on 2018-10-12
In case you haven't tried these ideas ... I had an issue like this a few weeks ago.  The mouse was always bouncing around even when nobody was in the room. It tended to move to the right-hand edge, but not always.  The mouse was dirty.  I cleaned it out - lots of junk in there. Lots, more than I thought possible. That didn't fix it.  Swapped in a newer mouse and that fixed it.  No issues since.

The original mouse,a logitech, was from 1999. The newer mouse is from 2007-ish, but I'd never used the newer mouse.

Also try rebooting the system.  Last weekend, a different system had about 5 keys stop working after an update.  I usually wait a day before rebooting. The reboot made those keys work again.  I'd never seen something like that in 20+ yrs.  I generally only reboot when necessary for most of my systems.  And for my laptop, I shutdown whenever leaving a location (work, home, hotel, conference).

---

### Post by antisthenes2 on 2018-10-13
Before enabling the software cursor, the mouse cursor behaved normally, so it seems likely that the problem is related to the switch to the software cursor.

---

### Post by antisthenes2 on 2018-10-18
Bump.

---

### Post by antisthenes2 on 2018-10-24
Any other ideas?

---

### Post by antisthenes2 on 2018-10-30
So, I've tried the following two common solutions found online:

1. Open System Settings > Displays.  In the Displays window, you will see an Unknown monitor.  Click it and disable it.

2. Running gsettings set org.gnome.settings-daemon.plugins.cursor active false

Neither worked. The system is fully updated.

I'd appreciate some suggestions, as it's quite difficult to use the OS as it is.

---

