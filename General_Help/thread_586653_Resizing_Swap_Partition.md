---
title: "Resizing Swap Partition"
date: 2007-10-22
forum: General Help
---

### Post by FrankP on 2007-10-22
Right, complete Linux noob here more or less.

When I installed Ubuntu I gave it a 2GB swap file. Now, I already have 2GB of quite good RAM as it is, and me back then didn't think anything of it. Now, I want to shrink that swap to 512mb and give my main partition (labelled ext2 I think) another 1.5GB of space.

I've installed GParted, and all the partitions are 'locked'. How do we go about unlocking them, deleting the swap file and creating a new one?

---

### Post by Arwen on 2007-10-22
Why not using GParted Live cd?I've never had a "locked partitions" issue using that and I have done really creepy things when partitioning in cases of multiple booting..

---

### Post by logos34 on 2007-10-22
Locked means mounted.  You can't resize mounted partitions. 

Download the [Gparted live cd]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") and boot from that.

---

### Post by FrankP on 2007-10-22
Thanks for both your replies, much appriciated.

Before you replied however I did an expiriment. As I've got my Ubuntu live CD still, I booted straight from that and launched GParted. Only the swap space was mounted. I right-clicked, and clicked "swapoff" (hence disabling the swap, I suppose). I resized it to 512mb, then applied it. Then, finally, swapon again.

However now I have 1.46GB "unallocated" space, and I GParted won't let my ext2 get any bigger via the "Resize/Move" dialog. It seems to have reached its maximum limit, however, we still have this unallocated space...

How do we transfer that space to my ext2 partition (the one with Ubuntu on it)?

---

### Post by FrankP on 2007-10-22
I may have cracked it myself actually.

Just needed to move the unallocated space directly below the ext2 partition, then GParted let us add the extra space. Its resizing as I type this.

Cheers All!

---

### Post by logos34 on 2007-10-22
> **FrankP said:**
> I may have cracked it myself actually.

Just needed to move the unallocated space directly below the ext2 partition, then GParted let us add the extra space. Its resizing as I type this.

Cheers All!

That's why I suggested the Gparted Live CD--it has the latest version which allows you to expand from the left or right.

---

