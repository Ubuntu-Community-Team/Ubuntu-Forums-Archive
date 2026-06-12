---
title: "Help, unable to start Gnome Panel !"
date: 2006-12-22
forum: General Help
---

### Post by tefflox on 2006-12-22
I install updates almost every day, and until now I've taken for granted that they will always work, but now I'm in the Failsafe Gnome session, trying to figure out why the Gnome Panels will not load.  The failsafe sessions tells me that the last error was "unable to find the message bus".  If I recall, one of the updates installed this morning was a Gnome panel update.  Is there a way to delete that update?  Thanks for your help.

---

### Post by tefflox on 2006-12-22
Here is the error I get.  I will be reading the man pages.  Any help is appreciated..

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by beerorkid on 2006-12-22
```
killall gnome-panel
``` might work.  But something must be mucked up if they are not showing up at all.

---

