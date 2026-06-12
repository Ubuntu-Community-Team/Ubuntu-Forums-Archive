---
title: "Any steps needed for SSD Optimization?"
date: 2013-11-21
forum: General Help
---

### Post by jCjQszKMO5JH on 2013-11-21
Hi there. Long time Ubuntu user but unfortunately I messed up when trying to merge my accounts with SSO. Oh well!

I haven't used a laptop with an SSD in some time. I think it was 9.10 or 10.04 and I remember that a number of optimizations were needed for SSDs to increase their life expectancy and performance. From searching (here and on the internet in general) I saw a lot of posts from back a couple years ago but not much recently. I seem to have come up with...


[LIST]
[*]Disable access time on your partitions ("noatime")
[*]Make sure the Deadline scheduler is used (I think 13.10 defaults to that...correct me if I'm wrong)
[*]Consider moving logs/temp files to a ramdisk
[*]Set up TRIM to run (at boot, or however you want to configure it)
[/LIST]

Are there any other suggested tweaks (both for performance and durability) when using 13.10 on an SSD?

---

### Post by oldfred on 2013-11-21
Ubuntu Aims To TRIM SSDs By Default
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY)

I converted from discard to using a daily cron task with fstrim.

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

If BIOS based you need AHCI on also for trim to work.

---

