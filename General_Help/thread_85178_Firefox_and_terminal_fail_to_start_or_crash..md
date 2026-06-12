---
title: "Firefox and terminal fail to start or crash."
date: 2005-11-01
forum: General Help
---

### Post by musther on 2005-11-01
Firefox sometimes fails to start, it simply says 'startng firefox' for a while, and then nothing, the same with the terminal program.  When firefox does load, it crashes on some pages, try to go to google for example, and just before the page renders, firefox closes, it's the same on most sites, but not all.  The cpanel part of a website I admin works fine.  

Anyone had this problem, or know what it might be?

Cheers

---

### Post by aysiu on 2005-11-02
Sounds like a corrupted profile. Go to /home/username and view hidden files/folders.
There should be a folder called .mozilla. Rename that to .mozilla_backup (do not *copy* the folder--*rename* it!)

Then, reopen Firefox. Does it work better? If so, find the bookmarks.html file from the backup folder and import it to Firefox.

---

### Post by wh0rd on 2005-12-25
That did the trick, but I'd just want to know what happened or what happens. How does the profile get corrupted if that's the issue. The issue keeps repeating even after I create a new profile.

---

### Post by Psquared on 2006-08-08
nothing like the "search" feature to solve a problem. I had the same problem with swiftfox and firefox. kept crashing and would not start due to a bad "theme" or "extension" (it started after i installed and tried to use a theme) now it works again. in the meantime i downloaded and installed the latest version of opera and dang if i don't think i like it better than konqueror or swiftfox.

---

