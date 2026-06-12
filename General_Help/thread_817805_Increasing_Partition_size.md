---
title: "Increasing Partition size"
date: 2008-06-04
forum: General Help
---

### Post by ktthomps on 2008-06-04
I am a new user to linux and am running Ubuntu version 8.04 dual booting with XP.  I created a partition for linux that was 25GB, and was wondering if there was any way in the future of possibly making this partition bigger. Any help would be appreciated.  Thanks.

---

### Post by chex_m8 on 2008-06-04
Yes, you can use a utility called gparted. It can resize partitions without destroying them. Back up your data first just to be safe, I've never had any problems though.

---

### Post by me208 on 2008-06-04
This is fairly simple:
[Download and burn the live CD for Gparted ]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779")

Then Boot into it. The Gparted window should open automatically. Shrink the XP NFTS partition then expand the Ubuntu ext3 partition. If Gparted won't let you edit the partitions, unmount them by right-clicking on them in Gparted and selecting unmount. They should automatically remount and you should be able to edit them.

Hope this helps!

---

### Post by ktthomps on 2008-06-04
thanks for your help.  I'll have to try it out

---

### Post by avtolle on 2008-06-04
Just wanted to call your attention to the fact that enlarging a linux partition can only be done "at the end", not from the "beginning". You will need to keep that in mind when/if you decided to try to enlarge the Ubuntu partition.

[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) has some general and excellent information about partitioning in general.

---

