---
title: "screen saver not starting"
date: 2015-07-18
forum: General Help
---

### Post by decrepit on 2015-07-18
I'm using unity 14.04 with gnome screen saver installed. 
when I adjust it, I get a "daemon not running, would you like to start it?" message. Once I do that it works OK, but unless I do it doesn't make an appearance.
So how do I get the daemon to start automatically at boot?

---

### Post by decrepit on 2015-07-21
May be making progress, opened "startup application" then found xscreensaver in /usr/bin/X11 added that to the startup apps list, we'll see if that works next time I boot up.

---

### Post by decrepit on 2015-07-21
Nup didn't work, but if I right click on xscreensaver and select "run" then it works. So why isn't it working in the start up list??
Any body

---

### Post by CantankRus on 2015-07-22
Do you want to run the default gnome-screensaver which is just a simple screen blanker and locker or
are you wanting to install xscreensaver which provides screensaver images?

Haven't looked at screensavers for a while but I believe you need to remove gnome-screensaver
for xscreensaver to work.

---

### Post by decrepit on 2015-07-22
Thanks CantankRus, yes I'm trying to get a slide show going, we enjoy looking at out travel pics when not using the pc.
I'll try uninstalling Gnome Screensaver and get back here.

Yep, thanks mate that seems to have worked!

---

