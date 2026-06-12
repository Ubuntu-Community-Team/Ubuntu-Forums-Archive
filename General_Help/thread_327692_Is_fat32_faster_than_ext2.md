---
title: "Is fat32 faster than ext2?"
date: 2006-12-29
forum: General Help
---

### Post by ahaslam on 2006-12-29
I've just got a Western Digital Passport (external usb hard drive). It came formatted as fat32 & data transfer was blisteringly fast (about 5 mins to transfer 5 gigs) but it's major downfall was the 4GB file size limit. Wanting to store some DVD iso's, I formatted it as ext2 but there seems to be less performance. I'm currently copying my 10GB backup partition, it has been over 20 mins & it's still going. 

Anyone else experience this, any suggestions?

Tony.

---

### Post by linuchsan on 2006-12-29
Try the xfs file system. I use it for tv recordings, without frame drops.

---

### Post by ahaslam on 2006-12-29
XFS does seem to be the best all round/performance FS, I use it for my root & home partitions, but I don't think it's suited to an external usb HD. XFS partitions can't be resized/moved in Gparted and there's no Windows support if friends want any of my files.

Tony.

---

### Post by Sef on 2006-12-29
> XFS does seem to be the best all round/performance FS, I use it for my root & home partitions

XFS is nice, but be sure to have back ups of all your files.   It is easy to have it crash and have to reinstall the os.

---

### Post by hikaricore on 2006-12-29
You can speed up ext2/3 a little bit by mounting it with the "noatime" option, but I don't know how to tell you to do this for an automounted usb drive.

---

### Post by ahaslam on 2006-12-29
> **Sef said:**
> XFS is nice, but be sure to have back ups of all your files.   It is easy to have it crash and have to reinstall the os.
I have been using XFS for some time with different distro's and no problems have ever arisen. 
The purpose of the external hard drive is to keep backups, purely because of my constant tweaking.

Anyway is it me, or is fat32 faster than ext2?

Tony ;)

---

### Post by dcstar on 2006-12-30
> **Anthony Haslam said:**
> 
......
Anyway is it me, or is fat32 faster than ext2?


Primitive filesystems can be faster than those that are far more resilient and feature-rich.

If you made it a DOS filesystem it may even be - initially - quicker, just take that early gain into account when it becomes fragmented over time, or a short power outage at the wrong time totally corrupts it and you lose data........          :(

We won't even mention the total lack of security in FAT32.............

---

### Post by ahaslam on 2006-12-30
Thank you, I believe that answers my question.

I've since read that fat32 also doesn't transfer the file permissions, I'd imagine that could have quite an impact on speed if you're transferring lots of files.

Tony ;)

---

