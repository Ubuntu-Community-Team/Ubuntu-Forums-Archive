---
title: "[SOLVED] Disk name variations break Thunderbird profile.ini pointer"
date: 2007-12-10
forum: General Help
---

### Post by gilf on 2007-12-10
Gutsy:

After tracking down  a problem with Thunderbird startups (Error message: Thunderbird is already running .....etc), I found that the problem was caused by the fact that Ubuntu mounts my external  hard drive partitions in a variable order as Disk-1 Disk-2 etc.

The Thunderbird profile.ini has a path pointer to the external HD partition where my mail files are. Since this partition can be named by Ubuntu as anything, depending on what gets mounted first on startup, Firefox loses track of where to go. It then throws up the "already running" message (which is incorrect -- there are no Firefox processes running).

If I manually correct the profile.ini path  to point to the current disk name with the mail files, I can start Thunderbird properly. This works until the next boot where drive names get juggled.

So, is there a way of solving this? 

Can a disk partition be assigned a unique name? Isn't there a fixed UUID now in Gutsy that is supposed to take care of this kind of thing?

Or as an alternative workaround, can I add multiple drive names to the path statement in profile.ini so that it checks in several places?

---

### Post by gilf on 2007-12-13
Anybody?

---

### Post by gilf on 2007-12-18
Solved:

[http://ubuntuforums.org/showthread.php?t=641810](http://ubuntuforums.org/showthread.php?t=641810)

---

