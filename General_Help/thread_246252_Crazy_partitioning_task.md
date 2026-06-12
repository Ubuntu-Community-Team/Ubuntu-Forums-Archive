---
title: "Crazy partitioning task"
date: 2006-08-29
forum: General Help
---

### Post by Burke on 2006-08-29
Ok, so my partition table is as follows: 
```

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        8287       12161    31125937+   7  HPFS/NTFS
/dev/hda2               1          17      136521   83  Linux
/dev/hda3              18         279     2104515   82  Linux swap / Solaris
/dev/hda4             280        8286    64316227+  83  Linux

Partition table entries are not in disk order

```

EDIT: If it's relevant, disk order is hda2, hda3, hda4, hda1.

You'll notice I have 4 primary partitions already. hda1 is Windows, hda2 is /boot, hda3 is swap, and hda4 is /. 

I want to create another primary partition to install another OS in. My only idea for this is to shuffle all of my Linux partitions into a single extended partition, which doesn't sound easy. 

How should I approach this problem? (I'm not deleting Windows -- I do need it occasionally ;)  )

Thanks in advance.

---

### Post by CameronCalver on 2006-08-29
have you looked a gparted you could create a extened partion and put all the other partions into that one and then that all good

---

### Post by Burke on 2006-08-29
okay, so I'd have to delete my swap partition temporarily to do that... Can I unmount swap somehow and do without it, or is it critical to Linux?  Should I do this from a LiveCD or Partition Manager in Windows instead?

EDIT: One other question... Windows is my bootable partition, but GRUB loads... If grub changes places, will OSes be unbootable?

---

### Post by mssever on 2006-08-29
To unmount swap, type sudo swapoff -a. To re-enable it, type sudo swapon -a. As long as you can get by with only the RAM installed in your machine, you'll be fine.

---

### Post by RRS on 2006-08-29
> **Burke said:**
> okay, so I'd have to delete my swap partition temporarily to do that... Can I unmount swap somehow and do without it, or is it critical to Linux?  Should I do this from a LiveCD or Partition Manager in Windows instead?

EDIT: One other question... Windows is my bootable partition, but GRUB loads... If grub changes places, will OSes be unbootable?

Diss-abling and deleting swap won't hurt anything but may slow the system down a bit depending how much ram you have.

Deleting the swap partition and using the space to create an extended partition shoudn't affect grub as the partition #'s won't change and any new logical partitions created in the extended partition will begin numbering from hda5.

You'll need to parttion from a live cd as gparted running from your OS won't be able to modify any mounted partitions, only display them.

I doubt using the windows utility is a good idea as it may have problems properly recognising the ext3 file system and want to reformat everything.

Gparted is available [here]("http://gparted.sourceforge.net/livecd.php") as a standalone live cd and seems to work better then the version on the Ubuntu live cd.

A screenshot from gparted (apt-get if you haven't allready) may help if you have have other questions.

---

### Post by Burke on 2006-09-01
problem solved, thanks.

---

