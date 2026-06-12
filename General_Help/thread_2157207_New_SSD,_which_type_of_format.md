---
title: "New SSD, which type of format?"
date: 2013-06-24
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-06-24
Hi All,

I have a new SSD on order, which should be here any day now. I've been trying to figure out which format to use on the new drive.

Note that this is for a Ubuntu only machine, which will never see Microsoft OS(s). I might dual boot with another 'buntu flavor or version.

I don't do fancy stuff, I just need 'buntu to run without the latest and greatest wiz bang fanciness.

I believe my choices are ext2, ext3 or ext4.

Is there a modern up to date tutorial on how to prepare a new SSD for use by Ubuntu??? Virtually all such material I've been able to find on the forum concerns windows/ubuntu dual boot.....and I do not want to handicap myself by making a Microsoft friendly system.

TIA

Art

---

### Post by oldfred on 2013-06-24
I was hoping to build a new system with UEFI soon after I got my SSD, so I used gpt partitioning, ext4 but turned journaling off.

 [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
This user suggests soem things differently than I did.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

      
 fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 

   noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)

I use trim with settings in fstab, but this says not to, but use fstrim.

 Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

Or some of the newer info seems to be different than what I found just a year ago. But part of it is the newest SDDs are better.

---

### Post by goodbye-windows(tm) on 2013-06-24
Hi Fred,

I see your posts all over the forum, you've helped SO MANY people. Thanks so much for being there.

I do have a 64 bit system and the new SSD is a Samsung 840 (128GB). I'm not sure how the drive will be configured by Samsung when it arrives however.

GPT sounds like one of those enhancements a non technical person such as myself should avoid. My motherboard is limited to SATA II transfer rates, so it is slightly aged (Asus). Should I still convert to GPT? GPT sounds like it's more appropriate for those users with multi terrabyte drives-which is not me::>

With the motherboard limitations I have, would GPT really make any major difference(s)?

TIA

Art

---

### Post by oldfred on 2013-06-24
I do not think gpt makes any real difference. It is required for UEFI and for drives over 2TB, but not required anywhere else. But MBR(msdos) is over 30 years old. That makes it well understood, like the 4 primary partition limit but getting old.

I only used gpt to learn about it. Once I created it I do not see any difference. I have used it since 10.10 on one small 160GB drive, on a flash drive just to see if it would work (it did) and on my SSD. 

If you know and understand MBR then stay with that.

---

