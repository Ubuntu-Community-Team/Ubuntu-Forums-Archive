---
title: "compiz destroyed X - how to repair?"
date: 2007-11-12
forum: General Help
---

### Post by DarkerStar on 2007-11-12
I tried to install compiz on Gutsy, and it would not start. So i tried removing it, then restarting my X server, and now nothing is working properly. I cannot open more that one window at a time, i cannot change the resolution to anything buy 1024x768 or it only takes up 1024x768 of the screen and leaves the rest blank. When i try the show desktop button, it tells me that X isn't running. Everything is dead slow now, too.

I tried to repair X by following some instructions in another thread here (i can't give you the link because i cannot switch to another window) - basically i used dpkg-reconfigure to reconfigure the X server to its defaults, and now /etc/X11/xorg.conf is back to the default (which worked before), but still nothing else is working.

Can this be fixed without having to reinstall ubuntu completely?

---

### Post by DarkerStar on 2007-11-12
I got the window manager running - manually. So at least the operating system is usable again.

But everything is still dead slow. How can i get all of that stuff - X, the window manager and so on - back to what they were when Ubuntu was installed.

---

### Post by 1337455 10534 on 2007-11-12
Depends on how many apps and documents you have on there. I suggest a clean install.... Nothing like a couple of those to keep the shrink away :lolflag:..
How did you get the gtk-wind-decorator (or is it emerald) working? emerald --replace or something like that?

---

### Post by DarkerStar on 2007-11-13
If i must, i must, i guess. I was hoping to avoid that.

I got the window manager to restart with x-window-manager. Just putting that in a terminal got the window manager running again, but everything was still dead slow, and i still could not change resolution.

---

