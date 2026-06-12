---
title: "Dual boot partitioning help needed"
date: 2007-01-11
forum: General Help
---

### Post by veganrailpunk on 2007-01-11
Hello there

I am dual booting Ubuntu 6.10 and Windows XP with Ubuntu on a 200gb drive (master) and windows on a 40gb separate hard drive (slave). It's all setup and works perfectly but now I wanna repartition my windows/slave drive to have windows installed on a 5gb ntfs part and have a 35gb fat32 storage part so I can share files between the os's. I only use windows for a handful of things and would rather not waste the storage space!

My slave currently has a 5gb ntfs partition with windows and 35gb unallocated but windows doesn't seem to want to let me set up that unallocated bit as a fat32 partion. Is it possible to do this somehow or will windows not let you have ntfs and fat32 running side by side ie do I have to have windows on a fat32 partition?

I installed bot OS's with the other drive unplugged  so I didn't have mixed OS's on the drive's MBR (I don't really know why (or what that means!) but I was told to do it).

I have installed a Windows fresh recently so it doesn't matter if I have to reinstall it.

Any help would be gratefully received!

Pete
xx

---

### Post by afbase on 2007-01-11
have you tried
```
sudo cfdisk
``` on ubuntu?  You should be able modify the 35 gb partition to fat32 that way if you have access to that 40gb hard drive and if they're aren't any write protections on it.

---

### Post by veganrailpunk on 2007-01-11
Thanx, just tried that but it only comes up with my hda partitions not anything on hdb. Can it be made to see hdb?

---

### Post by bodhi.zazen on 2007-01-11
Try cfdisk /dev/hdb

If you want graphical try gparted. You can install via aptitude/at-get/synaptic or try the live CD.

GParted:

	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by veganrailpunk on 2007-01-12
Ah brilliant thanx! :)

I used cfdisk to create the partition and then when I went into Windows (to load up the Live CD) it finally had an option to format it to FAT32 which it had never had when I had tried creating the partion using the Windows installer. One more reason why I'm loving Linux over Microsoft!!

Thanx
Pete
xx

---

