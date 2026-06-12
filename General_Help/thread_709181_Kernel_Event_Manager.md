---
title: "Kernel Event Manager"
date: 2008-02-27
forum: General Help
---

### Post by constchar* on 2008-02-27
On Gutsy Gibbon 7.10 I am unable to login when HAL is set to run on startup
and when I shutdown the X/11 server I see that Kernel Event Manager failed to start,
now this only happens when HAL runs on startup.

This started happening after I completely destroyed all traces of KDE3 and KDE4
and reinstalled KDE3.

Any ideas on how I can fix it?
Thanks!

---

### Post by constchar* on 2008-03-01
Ok I've discovered that "Kernel Event Manager" is actually udev and I did some playing around
in recovery mode and I notice that udev fails to start when I go to start it but if I click the "Stop"
button; it says it successfully stopped and now when I click "Start", udev actually starts properly
but otherwise when not booting in recovery mode udev always fails to start.

Anybody have any ideas on how to fix this?
Thanks!

---

