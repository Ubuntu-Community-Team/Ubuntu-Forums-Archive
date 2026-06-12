---
title: "partition names"
date: 2020-02-03
forum: General Help
---

### Post by cmcanulty on 2020-02-03
I recently removed windows 10 from a dual boot and so my partitions changed. Is there any way to get my 2 partitions renamed to sda1 and sda2? I would like them both to be primary partitions.
see the attached screenshot

[ATTACH=CONFIG]284960[/ATTACH]

---

### Post by yancek on 2020-02-03
You can't just rename partitions.  Your windows partitions were undoubtedly primary partitions so you now have the entire disk in an Extended partition on logical partitions.  You need to shrink the Extended and you can then create 3 primary partitions but would have to either install again or copy the files to the new partition which would also require modifying Grub and fstab.

---

### Post by CelticWarrior on 2020-02-03
And if take the road suggested above it would be much simpler to convert the drive to GPT and reinstall in UEFI mode.

---

### Post by cmcanulty on 2020-02-03
ok thanks I will wait until the next LTS















l

---

### Post by Impavidus on 2020-02-04
It is possible to rewrite the partition table without moving the data, but I don't know any tools that can do it for you (they probably exist) and I don't know enough about the internals of partitioning to tell you with confidence how to do it manually. There's not much benefit in changing to primary partitions anyway.

---

### Post by mdurham on 2020-02-05
It can be done with 'fdisk' probably best done from usb stick
run sudo fdisk /dev/sd(DISK THAT NEEDS REORDERING)
then 'm' for the menu
choose 'x' from the menu (expert mode)
then 'm' for the new menu
one of the entries will reorder the partitions nicely
I guess you will have to write the changes to disk, see the menu

---

### Post by oldfred on 2020-02-05
If you do reorder, you at minimum need to re-install grub.
And if you have used device like /dev/sdaX anywhere in system, all those entries have to be updated.

Better to wait until you do a new install.
And now if not using Windows in BIOS mode, consider gpt partitioning with a new install.
The only reason to use the now 35 year old MBR is if dual booting Windows on the same drive in BIOS mode. 
Windows requires gpt if booting in UEFI mode, but Ubuntu can boot in BIOS or UEFI mode from gpt.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

