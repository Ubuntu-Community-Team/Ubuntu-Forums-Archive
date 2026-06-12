---
title: "Locked screen"
date: 2014-05-21
forum: General Help
---

### Post by Softa on 2014-05-21
I've installed 14.04, but when my computer goes to sleep and I wake it up, I have to put my  password in again.  However, when I shut down and restart, the password is not necessary.

I opened a terminal, and typed xscreensaver-demo, to see if the screen was locked.  The check box is not checked.

How do I go about unlocking my screen?

---

### Post by sideburns on 2014-05-22
As the poster's brother and tech support guy, I'd like to mention that this is when the screensaver blanks the screen, as we don't have either sleep or hibernate configured on this desktop.

---

### Post by sideburns on 2014-06-05
New information: not only does this happen on her desktop, she has a netbook with Xubuntu (13.10) that's doing the same thing.  In both case, the checkbox for locking the screen is unchecked.  Is there some other setting or program that is overriding her settings?

---

### Post by Toz on 2014-06-05
With 14.04, the new default screensaver is light-locker (xscreensaver is not installed by default). Did you install xscreensaver? If so, did you uninstall/disable light-locker? The symptoms you are experiencing could be the result of two screensaver applications running simultaneously.

---

### Post by sideburns on 2014-06-06
We'd installed xscreensaver back when the desktop was still running 13.x.  Would light-locker be installed during the upgrade?  Please note that this is also happening on the netbook, running 13.10.  We'll check for light-locker on the desktop and disable it if it's there, and if this goes away, we'll remove it.  Thanx for the info.

---

### Post by Toz on 2014-06-06
> **sideburns said:**
> Would light-locker be installed during the upgrade?
Yes.  
> Please note that this is also happening on the netbook, running 13.10.
This might be a different issue since light-locker was not being used in 13.10, but have a look.

---

