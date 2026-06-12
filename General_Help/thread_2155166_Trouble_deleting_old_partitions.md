---
title: "Trouble deleting old partitions"
date: 2013-06-17
forum: General Help
---

### Post by JJossie on 2013-06-17
Hi,
I installed linux mint 15 and Ubuntu 13.04 on separate partitions, all under one extended partition (sda3). Linux mint was installed first, so it ended up on sda5. linux-swap is sda6, and ubuntu is on sda7. I decided I liked ubuntu better, so to regain space, I want to delete the partition with linux mint and let the ubuntu partition fill in the free space. I tried using gparted to delete sda5, but it gave me the message "Please unmount any logical partitions having a number higher than 5". Well, none of the partitions are even mounted except sda7, because ubuntu is running off of it (it says mount point is /). I tried unmounting it anyway and it gave me the message "The partition could not be unmounted from the following mount points:

/


Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually."
Now what do I do? I just need to get rid of sda5 to free up space.

---

### Post by Cheesemill on 2013-06-17
You can't unmount partitions when they are in use.

Boot from a Ubuntu Live CD and run gparted from there.

---

### Post by oldfred on 2013-06-17
+1 on Cheesemill's suggestion of liveCd.

Every logical partition is part of the extended partition. So any mount of a logical partition mounts the extended partition so you cannot do anything inside the extended partition.

Even with liveCD, it may mount swap, so you have to click on swap in gparted and right click swap-off.

---

### Post by QIII on 2013-06-17
It may go without saying, but...

Be sure you do good backups before launching into this.  We all make mistakes!

---

