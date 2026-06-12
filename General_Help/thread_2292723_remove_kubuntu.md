---
title: "remove kubuntu"
date: 2015-08-30
forum: General Help
---

### Post by m3t3ors on 2015-08-30
i had a dual boot system, windows 7 and ubuntu. then i decided id give kubuntu a test drive. so its now a triple boot system. after testing it for a few week id rather stick to ubuntu and windows. id rather give the space to ubuntu so
hows the best way to remove kubuntu and give ubuntu the space
thanks for any help

---

### Post by yancek on 2015-08-30
Simply format the Kubuntu partition and create a mount point for it to use it as a data partition then mount it.  If you want it permanently mounted, then you need an appropriate entry in the /etc/fstab file.  If it is contiguous to the Ubuntu partition, you might be able to extend the Ubuntu partition to include the Kubuntu partition but format the Kubuntu partition first.  Can't be any more detailed with the information you posted.  Post the output of:  sudo fdisk -l(Lower Case Letter L in the command) and indiate which partition contains Kubuntu.

---

### Post by m3t3ors on 2015-08-30
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1ca6ffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   194634682    97316317+   7  HPFS/NTFS/exFAT
/dev/sda2       194635774   488396799   146880513    5  Extended
/dev/sda5       291325952   480151551    94412800   83  Linux
/dev/sda6       480153600   488396799     4121600   82  Linux swap / Solaris
/dev/sda7       194635776   291325951    48345088   83  Linux

Partition table entries are not in disk order


think /dev/sda5 is kubuntu

---

### Post by grahammechanical on 2015-08-30
I would like to add one small point. If Kubuntu was installed last then its Grub is in charge of the boot process. Delete or format the Kubuntu partition and the Grub menu will not be able to load either Ubuntu or Windows. So, load Ubuntu and assuming that you only have one hard disk run this command:

```
sudo grub-install /dev/sda
```

That should put Ubuntu back in charge of the boot menu. After removing Kubuntu load into Ubuntu and run this command:

```
sudo update-grub
```

That will remove Kubuntu from the Grub boot menu list of options.

Regards.

---

