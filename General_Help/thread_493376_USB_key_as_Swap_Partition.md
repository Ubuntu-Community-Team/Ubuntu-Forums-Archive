---
title: "USB key as Swap Partition?"
date: 2007-07-05
forum: General Help
---

### Post by kingbabi on 2007-07-05
Hey, I wanted to know how I would use a USB key as swap instead of a partition on my hard drive. I used the partition manager to format the USB key as linux-swap (think windows readyboost), but I'm not sure how to direct Ubuntu to use the key instead of the partition I already have set up. How would I go about doing this?

---

### Post by limbourg31 on 2007-07-05
yes, look at this lifehacker article [http://lifehacker.com/software/featured-linux-download/speed-up-your-linux-box-with-a-thumb-drive-274911.php](http://lifehacker.com/software/featured-linux-download/speed-up-your-linux-box-with-a-thumb-drive-274911.php)

---

### Post by Tweenk on 2008-05-11
The guy in the article didn't swapoff his HD, so the system might have been using disk swap anyway.
BTW, ReadyBoost is a bit different than just using the flash drive as swap. It is more like write-through swap cache, because you can unplug the USB drive without crashing the system. Additionally, instead of making a swap partition on the USB drive directly, I would create a log-based filesystem like JFFS, LogFS or YAFFS on it and then use a swapfile. Otherwise the USB drive would die pretty fast.

---

