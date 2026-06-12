---
title: "No Free Space left on partition"
date: 2007-02-05
forum: General Help
---

### Post by chcwell on 2007-02-05
Near the bottom of the Nautilus panel, it displays that I only have 175mb of Free Space remaining, however, if I open the Disk Usage Analyzer, it says I'm using 94.6% (59.4gb used and 3.4gb available).  If I use Disk Usage Analyzer to scan / it only totals roughly 33gb of data.  The partition totals 62.8gb. Where has all my free/available space gone? These numbers don't add up.

---

### Post by melancholeric on 2007-02-05
Because users can't see, or use, all the space there is. Linux needs some free space on the disk to simply be able to boot. So, I think some 5 % is spared for that. The saved space is available to root but you'd be well adviced to not use it because that can render your machine unusable.

---

### Post by vigleik on 2007-02-05
ext3 reserves about 5% of the space to root in case you run out of space, so you will still have enough space for the operating system to run. That's probably why your numbers don't add up.

---

