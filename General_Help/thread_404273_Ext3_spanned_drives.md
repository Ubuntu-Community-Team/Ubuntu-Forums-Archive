---
title: "Ext3 spanned drives"
date: 2007-04-08
forum: General Help
---

### Post by DannyW on 2007-04-08
How would I go about creating a large volume which spans across several partitions or physicsal disks.

So I could say have /mnt/storage/ which is a 500GB volume spanned across a 200GB drive and a 300GB drive.

I guess many people must do this, and I've looked around the forums, wiki and google, but I guess I'm just searching for the wrong thing. Can anyone suggest a method for doing this?

Thanks,
Danny

---

### Post by kidders on 2007-04-09
Hi there,

What you're describing is called **RAID 0**. While it's very easy to do, I can't say I would recommend it...[LIST]
[*]It's almost never necessary. The only reason for using RAID 0 that comes to mind is to store extremely large files (ie bigger than your individual hard disks), which Ext3 is unsuitable for anyway.
[*]The result would be a filesystem that is 100% more likely to fail, in which event, all data would be lost.[/LIST]Could you describe the reason you want to use striping? Perhaps there is a safer alternative. For instance:
[LIST=1]
[*] Perhaps you don't actually need both partitions (or disks) to be part of the same filesystem at all. Many Linux installations are spread across multiple individual filesystems as a matter of good practice.
[*] If you *do* require one large filesystem, introducing some redundancy (eg RAID 1 or RAID 5) would offset the massive increase in failure probability. In the example you suggested, half a terabyte is an awful lot of data to be storing without protection.[/LIST]

---

