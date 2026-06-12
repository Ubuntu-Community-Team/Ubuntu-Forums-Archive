---
title: "MDADM/RAID-5 Slow Write Performance"
date: 2018-08-07
forum: General Help
---

### Post by iry100fan on 2018-08-07
Hi Everyone,

I'm running Ubuntu 18.04 (64-bit) on a Ryzen 7 2700X system with (3) Western Digital 6TB Red drives configured as RAID-5 using software RAID (MDADM).  The read speeds are reasonable (~260MB/s) but the write speeds are terrible (~8MB/s).  I understand that RAID-5 parity calculations are computationally intensive but during writes my CPU utilization never goes above 1.0% on any core.  It just seems to me that I should have more then enough processing power to warrant better write speeds.  I have seen numerous posts about increasing the cache size, but as expected, that only results in a temporary increase in write speed.  I have also tried increasing the "speed limit" settings under /sys/block/md0/md and /proc/sys/dev/raid/ without any change in performance.  I know this topic has been asked multiple times before but I can't seem to find a good solution or explanation.  Can anyone shed some light on what I am seeing.

Thanks.
-Brian

---

### Post by springshades on 2018-08-09
Have you tried something like this?

[https://ubuntuforums.org/showthread.php?t=1494846](https://ubuntuforums.org/showthread.php?t=1494846)

I'm not saying to run the script as-is because it's old enough that some of the commands may not even work anymore. However, you can follow along with the gist of the script.

I've never gotten much out of the speed limit setting, but the stripe cache size has always made a difference and the tune2fs settings seem to make a difference sometimes.

The other possibility is that you just aren't writing in a way that performs well on HDDs. Writing tons of small files tends to be pretty awful no matter what you do.

---

### Post by iry100fan on 2018-08-12
Hi [COLOR=#000000]springshades,

Thanks for the reply.  [/COLOR]I'll take a look through the link you posted and see if I can learn anything.

---

