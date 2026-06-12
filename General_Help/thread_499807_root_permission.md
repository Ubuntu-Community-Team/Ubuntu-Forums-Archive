---
title: "root permission"
date: 2007-07-13
forum: General Help
---

### Post by Nessa on 2007-07-13
A few hours ago, freed up more that 60GB of my 80GB drive. It's in ext3 format. When I try to copy/save files onto it, I get an error. "You do not have permissions to write to this folder."

The NTFS drives are working fine. It's the ext3 one that I can do anything with now. Any ideas?

---

### Post by mikewhatever on 2007-07-13
Is that the drive with Ubuntu installed on? Are you trying to copy stuff to the / directory? What happened since you freed the space? You obviously had permissions to delete 60 GB of files.

---

### Post by Nessa on 2007-07-13
I didn't delete anything. I bought an 80GB drive for just for ubuntu. I used the live cd to resize/add a partition. [10+GB ubuntu] [60+GB empty space] [swap]

I have some files on my external usb drive that I want to copy onto my free space in ubuntu. No problems mounting/unmounting the usb drive. But it is in NTFS format. Could that be a problem?

But so far the message just indicates something about permissions. And I don't know how to change read only to read/write.

---

### Post by mikewhatever on 2007-07-13
I am confused. If you wanted to write to the external ntfs formated drive, Ubuntu would need ntfs-3g package installed from the repositories. That is a driver to enable the write support for ntfs. You should be able to copy files from that drive however. Now, the question is, what is the format of the 'free space 60+' partition. If it is ntfs, the former applies, but if ext3, I am not sure.
To simplify the matters, can you post the output of the following command in the terminal 
> sudo fdisk -l

---

### Post by aysiu on 2007-07-13
One of these links should help:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by Nessa on 2007-07-13
There are files on the NTFS drive that I want to transfer/copy to the 60GB free partition in ext3 in ubuntu.

---

### Post by merlinus on 2007-07-13
You might try this:

after mounting the ntfs drive, in a terminal:

```

gksudo nautilus

```

That will allow you to run Nautilus as root, and you might be able to copy the files to your new 60G ext3 partition.

Also, look at the permissions for that partition, but as root you can usually do whatever you like.

Good luck!

-merlin

---

### Post by Saxomophone on 2007-07-13
Try logging in as root and check permissions on that 60gb ext3 drive?

---

### Post by Nessa on 2007-07-13
Without the external USB 80GB drive (NTFS)
> Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        4997    19655527+   f  W95 Ext'd (LBA)
/dev/hda5            2551        4997    19655496    7  HPFS/NTFS

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1275    10241406   83  Linux
/dev/hdb2            9919       10011      747022+   5  Extended
/dev/hdb3            1276        9918    69424897+  83  Linux
/dev/hdb5            9919       10011      746991   82  Linux swap / Solaris

Partition table entries are not in disk order



With the external drive....
> Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        4997    19655527+   f  W95 Ext'd (LBA)
/dev/hda5            2551        4997    19655496    7  HPFS/NTFS

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1275    10241406   83  Linux
/dev/hdb2            9919       10011      747022+   5  Extended
/dev/hdb3            1276        9918    69424897+  83  Linux
/dev/hdb5            9919       10011      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS



**How do you log in as root?** (I'll be reading the links. Thank you.)

Aysiu, you rock! Will this be like this forever or do I have to do this everytime?

---

