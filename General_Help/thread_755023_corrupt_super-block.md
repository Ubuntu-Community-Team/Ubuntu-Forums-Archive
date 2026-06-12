---
title: "corrupt super-block"
date: 2008-04-14
forum: General Help
---

### Post by jide on 2008-04-14
Hello,

I had already posted a similar problem at the "Hardware & Laptops Forum" - *[http://ubuntuforums.org/showthread.php?p=4707226#post4707226](http://ubuntuforums.org/showthread.php?p=4707226#post4707226)* but I thought General Help forum is more ideal for my problem.

I have both Windows XP and Ubuntu 7.10 in my HD. I repartitioned the HD using PartitionMagic 8.0 in Windows which failed. I later repaired it but since then I could not boot my Ubuntu. It produces this error during booting:
[B]/dev/hda7: 2414 files, 52997/610168 Clusters
Fsck.ext3: Bad magic number in super-block while trying to open /dev/hda7
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not Swap or UFS  or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock

e2fsck -b 8193 <device>

fsck died with exit status 9[/B]

I used **mke2fs -n -S /dev/hda7**to get the superblocks figures and tried 32768 to 1605632 (8 superblocks) without any success.

If I entered the command **sudo fdisk -l /dev/hda**, I get:
 /dev/hda7     (Start) 7924    (End) 9139   (Block) 9767488+   (ID)  b      (System) W95 FAT32

But when I tried **cat /etc/fstab**, I saw that it has the old record of my partitions and does not reflect the new partition which I added. So, how can I manually update and edit /etc/fstab and how do I obtain the new **UUID** of the new partition.

Actually, I do not know if updating the etc/fstab will solve the problem, so if anyone has the right solution I will grateful if he/she can drop few lines of advice.

Thanks

---

### Post by northern lights on 2008-04-14
Manually editing fstab is quite simple - open it as root, i.e. run```
gksu gedit /etc/fstab
```

---

### Post by az on 2008-04-14
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I suggest imaging your drive to a file on another (bigger) hard drive.  Then, try to rebuild your partition table using testdisk or parted.  See the link above.

If that fails, your partition has been eaten by Partition Magic.  You are not the first person to have this happen to you.  You may be able to recover lost files using data carving.  Either way, try to avoid writing to the device until you can image it.  If you work on the original without a backup you may make your data loss worse.

---

### Post by jide on 2008-04-14
> **northern lights said:**
> Manually editing fstab is quite simple - open it as root, i.e. run```
gksu gedit /etc/fstab
```

Sorry, I failed to mention that the manual editing of fstab is on the maintenance shell. You can only use sudo gedit /etc/fstab if you can log-in but in this case the ubuntu is not booting so you can only work from the maintenance shell.

Thanks.

---

### Post by jide on 2008-04-14
> **az said:**
> [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I suggest imaging your drive to a file on another (bigger) hard drive.  Then, try to rebuild your partition table using testdisk or parted.  See the link above.

If that fails, your partition has been eaten by Partition Magic.  You are not the first person to have this happen to you.  You may be able to recover lost files using data carving.  Either way, try to avoid writing to the device until you can image it.  If you work on the original without a backup you may make your data loss worse.

Thanks for the information. I will try it out tonight.

---

### Post by jide on 2008-04-15
> **jide said:**
> Thanks for the information. I will try it out tonight.

I tried but failed. So it looks like I will start a new installation. Since 3 days I have looked for a solution and tried many methods to no avail.

Thanks

---

