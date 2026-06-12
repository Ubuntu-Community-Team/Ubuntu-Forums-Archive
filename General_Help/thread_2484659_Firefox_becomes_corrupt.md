---
title: "Firefox becomes corrupt"
date: 2023-03-05
forum: General Help
---

### Post by bjngchn on 2023-03-05
Firefox left alone for a long period of time when JS is off, computer put to sleep.  Then firefox can stop working for no reason.   Sometimes I have to close one window and everything will be ok. Sometimes I close all windows, except one blank window, and frozen firefox is supposed to work but it doesn't.  Sometimes firefox tries to restart , and doesn't allow me to use it without restart. And of course I become suspicious, and just close firefox, not restart the way they force me to do it.   In short firefox not acting reasonably.  Also because of wrong hash code (it became wrong later) kubuntu updates not possible  anymore (but still forced by a program running out of my control), so why should I trust firefox updates, when kubuntu updates is not possible. And I don't want want firefox to update, they can do anything in the name of update, and run a process anytime in the name of update without my knowledge. How democratic is this.

---

### Post by guiverc on 2023-03-06
You've provided no OS/release details so we can't know what software stack you're using. You do mention Kubuntu (*thus KDE/Qt5/KF5 over a Ubuntu base*), but not the important release details.

I've personally got in the habit of closing `firefox` & `chromium` now that they're *snap* packages in my chosen release, as I find I have less issues on wake, and it only takes a fraction of a second on this box for them both to re-open (*but even if using a 2008 machine; I'll do the same; it just takes slightly longer to get it re-opened*).  Sure most wakes from suspend didn't have issues, but I've found this avoided the rare time when I had issues, **plus**this  also allows me to `snap refresh` prior to starting so I'm **not** annoyed by *an update is available & you have 14 days before*.... that I *often* got when I didn't close the browsers before suspend.

On later releases `firefox` is a *snap* package thus gets upgraded according to *snap* rules, which Kubuntu cannot control.  My chosen system is a multi-desktop, but I'm using Lubuntu currently & it's in the same *'boat*' in the Lubuntu team cannot control *snap* package updates.  My Lubuntu also shares `muon` & `plasma-discover` as software managers as Kubuntu & Ubuntu-Studio do.

---

### Post by bjngchn on 2023-03-06
Thanks, and does this mean, installing forefox separately would minimize such problems. And another most common problem is frezing firefox and computer just because of visiting a web page,  it is usually unstoppable.   I have lots of bookmarks which I don't want to lose (and which I access by search rather than browsing),  so switching to another browser or installation is not easy.

---

### Post by guiverc on 2023-03-06
I don't know what release you're talking about, thus I don't know if you're using a *deb* packaged version of `firefox` or a later release that uses a *snap* packaged version of `firefox`.  Thus I can only be generic with details, and highlighted the *swap* issue.

When you *release-upgrade* from a *deb* packaged version of `firefox` to *snap* packaged version, your existing settings will be imported automatically; but regardless they exist on your *file-system* which keeps a number of current profiles; so if a new one gets created; you can always grab details from your older *profiles*.  For my system (*which was only installed last month*) I can see the following

```
guiverc@d7050-next:~$   ls ~/snap/firefox/ -lah
total 40K
drwxr-xr-x 10 guiverc guiverc 4.0K Mar  2 08:41 .
drwx------ 24 guiverc guiverc 4.0K Jun 20  2022 ..
drwxr-xr-x  4 guiverc guiverc 4.0K Mar 22  2022 1115
drwxr-xr-x  4 guiverc guiverc 4.0K Mar 30  2022 1154
drwxr-xr-x  4 guiverc guiverc 4.0K Jun  4  2022 1406
drwxr-xr-x  4 guiverc guiverc 4.0K Jun 29  2022 1498
drwxr-xr-x  4 guiverc guiverc 4.0K Jul 13  2022 1551
drwxr-xr-x  4 guiverc guiverc 4.0K Feb 17 00:33 2356
drwxr-xr-x  4 guiverc guiverc 4.0K Mar  2 08:41 2391
drwxr-xr-x  4 guiverc guiverc 4.0K Mar 22  2022 common
lrwxrwxrwx  1 guiverc guiverc    4 Mar  2 08:41 current -> 2391
guiverc@d7050-next:~$ 
```

The profiles from before 17-February were from my older PC & just restores from backups.  What I showed *may* or *may not *match your setup, due to me not knowing your release, so the location where this data is stored on your system may differ (*why I started with the fact that you haven't said what release as we can only speak generically without this detail*).

On the few occasions where I've had a *bad crash* and firefox has started a new profile, I can use the detail in that directory to restore (*temporarily or permanently*) an older profile so I can get detail I can't recall to add it to my profile.

This box is dual boot; I have two releases on it (*jammy* [22.04] and *lunar*), and it's *lunar* I usually use, but on this *lunar* install I'm using a newly created profile, but on the *jammy* install I reverted to an older profile.  It took me only *minutes* to get the newer setup roughly identical to my older profile, if I exclude the URL history which I didn't try and restore... My intention was to decide which I preferred (*restored profile or new profile*) and make both installs the same, but after a few days of normal use my URL history was pretty much present anyway & I cannot pick which I prefer; so I never made them identical.

---

### Post by ajgreeny on 2023-03-06
You could also, with Firefox closed, rename the hidden .mozilla folder in you home and then start Firefox again.

Does Firefox now run properly? 
If it does then it points to a corrupt profile and it may simply mean that a fresh profile is needed into which you can import your bookmarks from the renamed folder.

---

