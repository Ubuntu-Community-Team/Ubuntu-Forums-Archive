---
title: "Screen Gets Fragmented"
date: 2019-12-19
forum: General Help
---

### Post by mcman56 on 2019-12-19
I have a new install of 18.04 on an NE71B following a hard drive failure.  The issue only started after the new install.  The screen will get randomly fragmented and shuffled.  This has only happened when listening to Amazon Prime Music with Firefox but that is most of what this computer is used for so I don't know if it would happen with other programs.  Reboot fixes it.  Close and restart Firefox worked once.  If this was windows, I would be looking to update the driver or find a different driver but I don't know how to do that here.  Are there any suggestions?

---

### Post by CatKiller on 2019-12-19
That looks like the video RAM is being incorrectly addressed for some reason.

As far as I can tell from a quick search that laptop uses rather old AMD graphics. I know that a bunch of stuff is continually being done to the AMD graphics infrastructure so you could try getting a newer version of Mesa from one of the PPAs that provides that to see if that helps.

---

