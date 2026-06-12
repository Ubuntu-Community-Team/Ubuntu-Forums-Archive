---
title: "Log In on USB drive insertion"
date: 2006-10-21
forum: General Help
---

### Post by HowardDrake on 2006-10-21
I had a whimsical notion about setting up a Ubuntu system for my family and in an effort to somewhat idiot-proof it, giving each family member their own USB thumb drive.

What I would like to happen is that when you plug in your USB drive the system logs you in, and maps the USB drive to your home directory, then when you log out, you yank the USB drive and the system is logged out until the next person logs in. Is such a thing possible or am I just insane :D

---

### Post by mjziegle on 2006-10-21
Interesting idea.  I would start attacking this problem by looking at my devfs rules since that's what's going to be activated when you plug in the stick.  The mapping portion could easily be handled by this so the user gets his/her own home directory on the flash disk.

I'm not sure if devfs could execute an arbitrary script for the login/logout function.

I also can't speculate on system performance with the flash.

---

