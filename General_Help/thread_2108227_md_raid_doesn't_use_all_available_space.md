---
title: "md raid doesn't use all available space"
date: 2013-01-24
forum: General Help
---

### Post by UglyBob on 2013-01-24
Hi guys!

A few days ago, I started upgrading my raid (raid 5) from using 4x1TB to 4x3TB. Never done this before, so it took a while. I replaced the disks one by one and rebuilt the raid in between as I read in some guide. All worked fine, except fdisk complained a little bit about my disks being very large. Didn't think much of it at the time. Now when I finally grew the raid and the filesystem, it's only 6TB. The raid was 2.7TB before, so I expected it to be 3 times bigger now. Could it be that fdisk didn't handle my 3TB disks properly?

---

### Post by SaturnusDJ on 2013-01-24
Looks like you are using MBR, while GPT is needed for that size disks.

---

### Post by UglyBob on 2013-01-24
> **SaturnusDJ said:**
> Looks like you are using MBR, while GPT is needed for that size disks.

Ok, does that mean I'm screwed or is it possible to do something about it without losing data? Do I have to remove one disk at the time and start over perhaps?

---

### Post by SaturnusDJ on 2013-01-24
Conversion is possible, eg:
- [https://bbs.archlinux.org/viewtopic.php?pid=623780#p623780](https://bbs.archlinux.org/viewtopic.php?pid=623780#p623780)
- [Google]("https://www.google.nl/search?q=linux+convert+MBR+to+GPT")

Not without risk.

---

