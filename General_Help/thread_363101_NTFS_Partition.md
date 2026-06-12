---
title: "NTFS Partition"
date: 2007-02-16
forum: General Help
---

### Post by birunda on 2007-02-16
So far I have been beaten up, for instance it took me two hours to get my ATI driver to work properly. 

I have a hdd that is partitioned as NTFS. I was able to mount the drive and access the information from it .  I cannot edit files by any means or download any data. The Drive is seems as file system and it is owned by root user so I cant change its permeations.  Does anybody known how to make that drive like that I can access it freely???

---

### Post by milton1 on 2007-02-16
there are ways to change the permissions, but ntfs is unstable at best for writing, and is read-only by default. You are better off making a fat drive that can be read/write for linux and windows (assuming you are keeping windows), or you could ditch windows and reformat the drive as ext3.

---

### Post by logos34 on 2007-02-16
linux does not natively support writing to ntfs...need a special driver (ntfs-3g).  Or else format  it as fat32.

---

### Post by vigleik on 2007-02-16
Install ntfs-3g. It's still in beta, but is considered reasonably stable. You can't expect writing to ntfs to work out of the box (though it might in the future) as microsoft keeps it secret how the file system works.

---

### Post by irw on 2007-02-16
ntfs-3g works fine for me, and despite the beta status, I have had no problems with it. 

That said, I now rarely access the NTFS partition, and the other partitions I have are FAT or ext3.  the NTFS will be dumped as soon as I get around to learning GNUcash or similar to replace MS money, then windows will be history ! :D

---

### Post by birunda on 2007-02-16
thx!! i dont have windows anymore so it will only be for linux. the drive is 500gbs and it is filled up with data so I cant format it ... do you think NTFS-3G will damage my NTFS partition?

---

### Post by irw on 2007-02-16
> **birunda said:**
> thx!! i dont have windows anymore so it will only be for linux. the drive is 500gbs and it is filled up with data so I cant format it ... do you think NTFS-3G will damage my NTFS partition?

It should not cause any damage.

however, a drive "filled up with data so I cant format it" worries me - do you have any sort of back up? 

It may that your best approach if you have any room on the disk is to:
1. defragment it, then reduce the partition size, create a new ext3 partition in the free space.
2. copy some of your data to this patition
3. reduce the NTFS partition
4. increase the ext3 partition
5. goto 2. 
and keep going round the loop until you have no ntfs partition left.  it may be time consuming, but would get rid of a file system type you do not need...

I used a similar approach (albeit on a slightly smaller scale - 100Gb not 500) using the 
[GParted live CD]("http://gparted.sourceforge.net/") without any data loss.

---

### Post by jvc26 on 2007-02-17
> **vigleik said:**
> You can't expect writing to ntfs to work out of the box (though it might in the future)
I fear that may well never be the case if Ubuntu continues to not distribute the non-free codecs with its distro.
Il

---

### Post by simonsphotos on 2007-02-17
> **irw said:**
> It should not cause any damage.

however, a drive "filled up with data so I cant format it" worries me - do you have any sort of back up? 

It may that your best approach if you have any room on the disk is to:
1. defragment it, then reduce the partition size, create a new ext3 partition in the free space.
2. copy some of your data to this patition
3. reduce the NTFS partition
4. increase the ext3 partition
5. goto 2. 
and keep going round the loop until you have no ntfs partition left.  it may be time consuming, but would get rid of a file system type you do not need...

I used a similar approach (albeit on a slightly smaller scale - 100Gb not 500) using the 
[GParted live CD]("http://gparted.sourceforge.net/") without any data loss.

I would not advise this a simple power cut and you can lose the lot unless of course you use and UPS and are 100 % sure of the software.

---

