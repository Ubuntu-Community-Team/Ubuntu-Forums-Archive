---
title: "Allocate more disk space to Ubuntu 18.04 server edition"
date: 2019-05-06
forum: General Help
---

### Post by glogs on 2019-05-06
I have a main ssd drive that I only partitioned enough room for ubuntu.  I left the rest unpartitioned and now would like to just have the entire drive as ubuntu. I have two additional zfs drives that are for storage and are mirrored and want to be careful that I don’t lose anything.  What are the steps necessary for this to work (FYI I am a new to command line and ubuntu). I looked on previous threads and read something about gparted and shrinking/increasing current partitions  ... but I think it was specific to a disk that had already been partitioned . Thanks

---

### Post by TheFu on 2019-05-07
/ shouldn't be over 25G. There are many reasons for this.

Why not add the SSD to your zfs pool or create another zfs pool just for it?

---

### Post by glogs on 2019-05-07
[COLOR=#DD4814][COLOR=#000000][TheFu]("https://ubuntuforums.org/member.php?u=1037685"): Interesting...[/COLOR][/COLOR]Thank you for the response.   Currently I have 1tb SSD that ubuntu is on (with minimal disk space) and the rest unpartitioned.  And, I have 2 X 3tb mirrored zfs drives.  Because the remainder of the SSD is smaller than the mirrored drives I probably should not add the SSD to the current pool (right?).  However, I could create a pool for data that I don't mind losing if somethings happens to the SSD.  So would I just zfs create pool on whatever amount of empty space on the ssd.  I don't recall if I need to pass it anything...like what part of the disk to create the pool.  What would be the command line input to do this?

---

### Post by TheFu on 2019-05-07
On Linux, I use LVM, not ZFS.  With LVM, I'd create a partition for all the remaining empty space on the HDD, then create a PV for that, Create a VG using the PV, then create LVs from the VG storage, as needed.

Regardless, I wouldn't actually allocate more than 80% of the total storage on the SSD to any LVs.  Turns tout that leaving 20% free on SSDs drastically extends the lifespan, at least on modern, quality, SSDs.  This week, I've posted my storage setup using lsblk, so you can get a feel for what I think is the best practice.  Look for "sda3_crypt" in my posts.  I've posted some of my other storage setups, which aren't ideal. They were started around 2010. Things have changed since then.

---

### Post by glogs on 2019-05-10
Thanks Ill check it out

---

