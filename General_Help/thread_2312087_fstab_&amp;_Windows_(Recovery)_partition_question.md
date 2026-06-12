---
title: "fstab &amp; Windows (Recovery) partition question"
date: 2016-02-01
forum: General Help
---

### Post by sonicwind on 2016-02-01
I'm carefully reading the MountingWindowsPartitions page on help.ubuntu.com and have one question.

I have Windows 7 and it has a Recovery Partition to recover to the original Windows setup. In Disk Management (where you look at partitions in Windows 7), it doesn't list a file system (NTFS, etc) for the Recovery Partition.

Will this partition be listed (with a UUID) if I do **blkid** in a terminal in Ubuntu? What file system is it?

Thanks guys.

---

### Post by yancek on 2016-02-01
There is absolutely no reason to mount the windows recovery partition in Linux.  It has only one purpose that it can be used for and you need to do it from windows.
On my HP with win 7, it is an ntfs filesystem and shows with blkid.  Does windows 7 show the filesystem type for it's other partitions?

---

### Post by sonicwind on 2016-02-01
Yes, it shows the partition type for all other partitions.

I'm not looking to mount it in Linux. I'm aiming to make sure none of my Windows partitions get mounted (and in fact get hidden) by the method described under Option 2 on the MountingWindowsPartitions page.

Thanks yancek.

---

### Post by Nuno_Abreu on 2016-02-02
I've mounted Windows partitions in the past with no problems - it didn't mess up the dual-boot install I had back then (remember it was XP and then 8).
As long as you don't mess around, you should be fine.
It is great to access them to fix some kind of configuration problem or even get to know suspicious files from people when they are not encrypted - with that, I mean recovering them before a great format. That's why it is always better to keep your collections on a separate partition to stop this hassle.

---

