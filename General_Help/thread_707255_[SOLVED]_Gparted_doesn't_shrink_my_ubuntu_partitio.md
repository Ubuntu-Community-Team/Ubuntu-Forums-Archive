---
title: "[SOLVED] Gparted doesn't shrink my ubuntu partition"
date: 2008-02-25
forum: General Help
---

### Post by ubsimonp on 2008-02-25
Hi community:

My pc only have a single 150G sata hard drive.

By using liveCD, I  installed ubuntu 7.10 to this hard drive, 140G as primary partition (JFS not ext03), 10G as swap. 

No dual boot, just pure raw ubuntu system. The whole system is running ok

The system is only installed basic ubuntu, no data, no heavy programs. From Gparted, I can see only 4G of primary partion is used, So I want to shrink the partition to 20G or so.

I used Ubuntu LiveCD to bootup, and make sure all hard drive partitions are unmonuted.

However, In the UI of Gparted, I can't change 140G to any other smaller number. I can change swap partition from 10G to 1G, after this, I can even increase 140G to bigger number, but still can not decrease the number.


Is there any way I can shrink this 140G primary partion (only 4 G is in using) to 20G?

Please help, thanks a lot.


Regards,
-Simon

---

### Post by kshane on 2008-02-25
Are you using GParted  from a bootable CD?  Some operations are difficult, at best, from within Ubuntu when using GParted.  Make sure you use GParted's bootable version.

Kevin

---

### Post by louieb on 2008-02-25
Sorry - GParted can't shrink a jfs partition.
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

---

### Post by ubsimonp on 2008-02-25
Thanks a lot louieb. 

I will rebuild and use EXT3 instead.

Regards,
-Simon

---

