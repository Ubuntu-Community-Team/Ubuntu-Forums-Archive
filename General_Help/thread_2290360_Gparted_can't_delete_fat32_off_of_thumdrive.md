---
title: "Gparted can't delete fat32 off of thumdrive"
date: 2015-08-11
forum: General Help
---

### Post by cranerja on 2015-08-11
Whenever I try to delete the fat32 partition that came on the thumb drive, gparted says it completed, but after it refreshes the partition is still there. It is read/write and I am able to put files onto it.

---

### Post by SeijiSensei on 2015-08-11
Just to make sure, you are doing the format as the root user, yes?

If you just want to delete the partition, fdisk is a lot easier.  "sudo fdisk /dev/sdX" to start it.  If there's just one partition, type "d" to delete it, then "w" to write the changes to the disk.  I'd then unmount the device, remove it from the machine, and reinsert it to see if the changes stuck.

---

### Post by cranerja on 2015-08-11
When I try that, it says "No partition is defined yet!" I think the problem lies within their being hidden partitions. What then?

---

### Post by Dennis N on 2015-08-11
To remove all existing partitions and remove all data from the flash drive, you can just use gparted and create a new partition table:
In gparted, be sure you select the correct device from the drive selector in the upper right before proceeding . Then from the Menu:
**Device > Create Partition Table**
A warning is shown that this will erase all data on the flash drive.
Chose the type of partition table you want to use from the list. After this, you can create new partitions with **Partition > New**

-----------------------------------------------------------------
P[315]

---

### Post by HermanAB on 2015-08-11
As usual, it depends...

If it is a thumb drive that you got at a trade show, then it may very well have a read only partition on it that cannot be deleted or changed.  I have one of those.  My guess is that this little controller chip has a special feature.

---

### Post by Dennis N on 2015-08-11
> **HermanAB said:**
> As usual, it depends...

If it is a thumb drive that you got at a trade show, then it may very well have a read only partition on it that cannot be deleted or changed.  I have one of those.  My guess is that this little controller chip has a special feature.

Wow. That's interesting to know. I have to buy mine at the store and haven't ever seen such a drive. Hope he doesn't have one of those!

---

### Post by SeijiSensei on 2015-08-12
Sounds like the kind of thumb drive that would be a nice home for Stuxnet.

---

### Post by cranerja on 2015-08-12
Guess I should have just tried a new parition table from the get go. It worked! Also, I have had thumb drives that do have those read only partitions that can't be removed. This is what caused my worry. Thanks all!

---

