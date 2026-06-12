---
title: "Chromium won't save settings"
date: 2012-12-06
forum: General Help
---

### Post by Stonecold1995 on 2012-12-06
I'm using Chromium 25.0.1323.1 (from ppa:a-v-shkop/chromium), and for some reason I can't change any settings.  For example, if I go to about:settings and try activating anything (say, "Enable phishing and malware protection"), if I refresh the page the change is undone.  Chromium doesn't have an "Apply" button, and this use to work in the past, but now it seems like Chromium simply won't save changes.  This also happens if I try to add a site to the JavaScript whitelist (I have JavaScript disabled on all sites by default).  Browser history seems to be saved though...

Why is this?  I can't seem to remember anything that could have caused it.  Checking syslog showed that it's not having problems with AppArmor, and ~/.config/chromium is owned by me, so it can't be a problem of permissions.  How can I get Chromium to save settings again?  I tried re-installing Chromium, and I tried deleting .config, but it didn't work.

Is anyone else having this problem with this version of Chromium?  How do I fix this, or should I just wait for an update to fix it?

---

### Post by Stonecold1995 on 2012-12-10
bump

---

### Post by CaptainMark on 2012-12-10
If your on version 25 your using the unstable branch of this ppa, uninstall chromium and delete ~/.config/chromium then switch to the stable ppa which carries version 23 and reinstall chromium,

---

### Post by Stonecold1995 on 2012-12-10
So it is just the Chromium version needs a but to be fixed?  I'll probably just wait until a fix rolls out instead in that case.

---

### Post by CaptainMark on 2012-12-11
But if you continue to use the unstable branch will always have a beta version of chromium and may experience unexpected bugs at any time, I'm not claiming it will definitely fix your issue but did you have a specific reason not to use the stable branch

---

### Post by Stonecold1995 on 2012-12-11
I just prefer the beta versions, I get access to new browser flags more quickly that way.  I haven't  had an update for a while though, so it's kind of confusing why it's taking so long.  Then again it's not the official PPA.

---

### Post by CaptainMark on 2012-12-12
No your right, its one programmer volunteering his free time to it, which is cool, if you insist on using unstable versions of any software you don't really have much room to complain when they don't work as expected, to each his own though I suppose

---

### Post by Stonecold1995 on 2013-01-11
Chromium hasn't updated for a long time.  Is this PPA no longer being maintained?

---

### Post by vasa1 on 2013-01-11
> **Stonecold1995 said:**
> Chromium hasn't updated for a long time.  Is this PPA no longer being maintained?
Did you contact the ppa owner?

---

### Post by CaptainMark on 2013-01-14
Possibly just another chromium ppa that has fallen by the wayside, apparently chromium is a hard project to package, so sooner or later the package maintainer seems to lose interest

---

### Post by justen_m on 2013-01-14
I just got "upgraded" from Chromium 22.X to 23.X, and I am no longer able to save Privacy settings. I check a box to enable to options, but they seem to get instantly cleared. This isn't an unstable beta branch I am talking about or some custom ppa. 23.X has been released. I tried creating a brand new profile, but that didn't help either. I'm running Ubuntu 12.10.

---

### Post by justen_m on 2013-01-20
I never figured it out. I installed Chrome. No problems so far.

---

### Post by ErickRibeiro on 2013-01-20
Problem occurs in Stable version too. I am using Lubuntu 12.10 and it does not save the settings. It is a bug. It's the version provided officially and I just upgraded my browser form 22.x to 23.0.1271.97 (Ubuntu 12.10 (23.0.1271.97-0ubuntu0.12.10.1))

I think the users have to file a bug, just like I did, it can be accessed at:
Top right Menu > About Chromium > Report Issue

I sent the report:
"Chromium doesn't save personl settings. If I go to top right menu > Settings, and make a change (for example, checking the "Search: Activate Google Instant" or "Initialization: Open new Tab") and refresh the page, the settings are unmade."

---

### Post by Stonecold1995 on 2013-01-31
It seems like now, after the update, settings won't even LOAD by themselves, it just presents a blank page.  The only way to view settings (which are still stuck on their default options and won't change) is to type something into the Search Settings bar and then delete it.

[http://www.pictureshack.us/images/10946_settings01.gif](http://www.pictureshack.us/images/10946_settings01.gif)

---

### Post by Stonecold1995 on 2013-02-03
Ah, another new problem arose with the latest update.  Not only are settings not being saved and they won't even appear without doing what I did in the GIF above, but also trying to clear any browsing data causes the whole browser to freeze!  I tried clearing my cache, and as soon as I pressed "OK" to clear it it simply stopped responding...

This is getting extremely frustrating...  Is there any easy way to compile from source, without having to go through all the hoops Chromium wants?

**EDIT:** Another update came out.  It seems to have fixed a few of the issues, but the primary problem of settings not being saved remains...

---

### Post by vasa1 on 2013-02-03
> **CaptainMark said:**
> Possibly just another chromium ppa that has fallen by the wayside, apparently chromium is a hard project to package, so sooner or later the package maintainer seems to lose interest
+1. Last I heard, someone from Canonical was going to handle updates of Chromium. But that was a while ago.

Edit: [https://launchpad.net/ubuntu/+ppas?name_filter=cmiller](https://launchpad.net/ubuntu/+ppas?name_filter=cmiller) has "chromium-browser-beta-daily" and "chromium-browser-stable-daily" but these are still version 24. Chrome stable, as defined by Google, is version 24. Chrome beta, as defined by Google, is version 25.

---

### Post by ErickRibeiro on 2013-02-03
Problems solved on Chromium 24.0.1312.56 Ubuntu 12.10 (24.0.1312.56-0ubuntu0.12.10.3)

---

