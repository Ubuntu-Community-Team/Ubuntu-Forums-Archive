---
title: "Booting Vista, Ubuntu, 2 Dell Partitions"
date: 2006-10-15
forum: General Help
---

### Post by detorovx on 2006-10-15
I'd like to select which partitions to boot from at start up, with Vista as the first choice to boot if no other selection is made after the alloted time.

Currently the computer only boots directly to Vista, there is no selection.

The Dell pc came with 1 Windows XP NTFS, 1 DellRestore, 1 DellUtility partition

Later I installed Ubuntu 6.06.1, partitioning the NTFS into two smaller partitions, 1 ext3 and 1 swap partition. In this case at power on I had a choice to boot from different ubuntu kernels and other os' and Windows XP if no other selection was made by a set number of seconds it would automatically boot with the latest ubuntu kernel. At this point I could no longer boot into the dell partitions using their preset keyboard shortcuts, I don't know any other way to do so.

I decided to test Vista and clean install it over the remaining WinXP partition. After that, I now have no other visible way of booting to other partitions. 

If I could at least get Vista and Ubuntu selectable I can be happy until it's necessary to run the dell partitions.

---

### Post by Kateikyoushi on 2006-10-15
Follow [this guide]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub") to restore your grub.

---

### Post by detorovx on 2006-10-15
Awesome, it's back to exactly how it was, so much that it still lists the Windows OS on my drive as Windows XP. Has not updated to reflect the change to Windows Vista. It boots to Vista just fine, there's just that missinformation on the grub list.

Now how would I go about getting those dell partitions bootable again and setting the Vista OS as the first option to boot from since it requires the most restarts... =p

---

### Post by Kateikyoushi on 2006-10-15
You can set Vista as the default OS in grub look at [these steps]("http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu").

I have no experience with dells so I also wonder how did it address those partitions.

Lets take a look at your partition layout, post the output of the following command.

```
sudo fdisk -l
```

---

### Post by detorovx on 2006-10-15
returned this, I'm going to set the default os after posting, I took too long to see the response

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       15802   126881370    7  HPFS/NTFS
/dev/sda3           18993       19452     3694950   db  CP/M / CTOS / ...
/dev/sda4           15803       18992    25623675    5  Extended
/dev/sda5           16307       18992    21575295   83  Linux
/dev/sda6           15803       16306     4048317   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

