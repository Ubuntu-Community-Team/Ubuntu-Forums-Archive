---
title: "Icons reverting to default gnome set instead of humility set."
date: 2008-04-28
forum: General Help
---

### Post by mcorcoran on 2008-04-28
The humility icon set (downloaded from Synaptic) used to work for me under gutsy but now certain icons (most notable the folder icons) are only displayed as their default gnome counterparts in Nautilus. I'm looked in /usr/share/icons and they from my limited knowledge they appear to be there. I've tried reinstalling the icon set and using a separate download version with no luck. All my other icon sets work fine. Is there someway to force gnome to use the Humility folder icons instead of the Gnome Defaults?

---

### Post by BandD on 2008-04-28
Gnome chooses what icons to use by filename.  It looks through your chosen theme (humulity in your case) for specific filenames.  If it doesn't find what it is looking for it moves on to the system defualt icons.  

Something seems to be screwy in Hardy (or possibly gnome 2.22) and the defualt gnome naming structure has changed for a few of the icons.  There really doesn't seem to be an easy fix for this, at least not yet.  It will take some work on your end to get it working.  

Basically what you need to do is open up an icon set that works and the icon set you want to work in Nautalus.  And go through the the folders in both and match up the file names, change whatever you need to in humlity to make it the exact same as the working theme.  It's tedious, but it seems to be the only way to make it work at present--until 1)this naming sturcture problem is resloved in Hardy or gnome, or 2)until the developers of icon themes become aware of this change and update their themes accordingly.

---

### Post by stansford on 2008-04-30
> **mcorcoran said:**
> The humility icon set (downloaded from Synaptic) used to work for me under gutsy but now certain icons (most notable the folder icons) are only displayed as their default gnome counterparts in Nautilus. I'm looked in /usr/share/icons and they from my limited knowledge they appear to be there. I've tried reinstalling the icon set and using a separate download version with no luck. All my other icon sets work fine. Is there someway to force gnome to use the Humility folder icons instead of the Gnome Defaults?


there are a couple of fixes here if you want them:

[http://ubuntuforums.org/showthread.php?t=731142&highlight=hardy+icons+don%27t+work](http://ubuntuforums.org/showthread.php?t=731142&highlight=hardy+icons+don%27t+work)

---

