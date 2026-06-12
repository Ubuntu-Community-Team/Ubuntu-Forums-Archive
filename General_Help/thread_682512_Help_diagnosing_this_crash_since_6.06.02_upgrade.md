---
title: "Help diagnosing this crash since 6.06.02 upgrade"
date: 2008-01-30
forum: General Help
---

### Post by aoakley on 2008-01-30
Since last week (which co-incided with the 6.06.02 upgrade but may not be related), I have been having frequent intermittent kernel panics and other crashes which result in a systems freeze and masses of console errors.

Example: [http://aoakley.com/misc/crash-20080130.jpg](http://aoakley.com/misc/crash-20080130.jpg)

I am not running GDM/Gnome or any desktop at the time. My system was stable prior to last week. However I do admit to having installed third-party software that isn't in official repos (such as Beryl).

How can I diagnose this please? I can't find anything relevent in the logs, probably because I don't know what to look for. I don't even know whether it is related to the 6.06->6.06.02 upgrade or is something else such as a hard drive failure (I have two pairs of RAID1 mirrors using EXT3).

If it is a hard drive failure (lots of mentions of kjournald) how can I identify which drive is failing please? cat /proc/mdstat either shows nothing abnormal, or the first array rebuilding which completes without problem (question still is, which of the two drives in the first array was at fault?).

Any help much appreciated, thanks.

---

