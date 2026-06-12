---
title: "Firefox partial lock of system after upgrade"
date: 2022-02-15
forum: General Help
---

### Post by cam17 on 2022-02-15
I was previously running firefox 96 when I received a restart firefox request from firefox itself. After the restart Firefox locked up with the firefox window running a quarter of the screen from its previous full screen and the tabs as well as the maximize button did not work. It disrupted the opening of other applications but not all. If I closed the windows process it restarted normally.

I have experienced this update problem before this version and don't like how it disrupted other applications. Anyone suggestions?

---

### Post by DuckHook on 2022-02-15
Backup your configuration, all of your bookmarks, extensions, history (if you want), then clear everything in FF cache and do a refresh: [https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings](https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings)

Alternatively, you can create another profile, then import your bookmarks etc into that. This method isn't as thorough as the refresh, but it is often enough, and it preserves your old profile just in case.

The principle behind both approaches is to reset to a clean state.
> **cam17 said:**
> …It disrupted the opening of other applications but not all. If I closed the windows process it restarted normally.

I have experienced this update problem before this version and don't like how it disrupted other applications. Anyone suggestions?
Disrupting other apps is a concern.

If the above measures don't work, then try disabling HW acceleration. FF misbehaving with HW accel was one of the problems that plagued my latest upgrade, but only on one older laptop. Everything else runs fine. You haven't told us your HW details, so this last is a bit of a shot in the dark.

---

### Post by Impavidus on 2022-02-16
Sounds more like a problem with the window manager than with Firefox itself. Window size and the effect of the maximise button (even the existence of a maximise button) are not under control of the application, but under control of the window manager. The application can only send kind requests to the window manager and await the results. The tabs however are controlled by Firefox.

Or it could be related to some library handling the interaction with the window manager that is used by Firefox and the other offending applications.

---

### Post by MAFoElffen on 2022-02-16
Well... My two cents. FireFox seems to do strange things during it's updates. On some of my systems, Most of the time, it's while I am on this Forum. Which I am on most of the time, but just by coincidence...

Then to be of more of an inconvenience and frustration, I'll be in the middle of a long response to a User... When all of a sudden, I can no longer type anything, nor change tabs... Sometimes, then I can't get to other windows that are open, nor go to activities nor even open a terminal session... I can get to a vtty session by hotkey to reboot...

Then on reboot, FireFox has updated versions, so was the culprit. It i snot that there was any problem, except that FireFox was updated and needed to restart. Sometimes FireFox will tell me that, but sometimes it just freaks out.

Yes it is some kind of BUG, but it has happened to me enough times over the years, that it is just more of an inconvenience and has been a part of life. Grrrr.

---

### Post by foxsquirrel on 2022-02-16
> **cam17 said:**
>  Anyone suggestions?

You are not alone on that, mine is locking up and frequently on ARM. It has been suspected of messing up the installation of ubuntu. Found that keeping the box off the internet  until Ubuntu is completely installed will work for the installation issue. Don't know for fact what is causing this, its just pure speculation regarding it messing up the installation on ARM platforms. Firefox its self locking up is real and frequent, Pi 4 and VIM3.

---

### Post by cam17 on 2022-03-09
Mafolellfin. I think you view is correct. i tested another browser and only Firefox exhibited this behaviour.

---

