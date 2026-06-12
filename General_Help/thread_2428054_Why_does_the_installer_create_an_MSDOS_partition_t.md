---
title: "Why does the installer create an MSDOS partition table?"
date: 2019-09-29
forum: General Help
---

### Post by GhX6GZMB on 2019-09-29
During installation, I noticed that the installer creates an MSDOS partition table, although the entire disk is partitioned for Lubuntu and formated as ext4.
Why is this, please?

Thank You.

---

### Post by Dennis N on 2019-09-29
Did you select the installation option to Erase Disk and Install Ubuntu? Then it will repartition first before installing, erasing any programs on it. MS-Dos is the default partitioning for BIOS booted installer with this option.

---

### Post by ajgreeny on 2019-09-29
I'm not sure I fully understand your query but if you choose the option to install the system using the whole disk, ie, the default installation, you get no chance to make changes to anything related to the partitions, formatting, or filesystem types used; everything will be done automatically, with no reference to your preferences

If you already have partitions on the hard disk which you wish to use, or reuse if reinstalling, you will need to choose the "Something Else" option at the disk preparation stage.  I can not remember whether that gives you the option to create or change the partition table type, but I  think that is something that is only available as a separate activity by using gparted (from the installation medium) or command line.

---

### Post by GhX6GZMB on 2019-09-29
I've done a completely clean installation, with a previous sudo mkfs.ext4 /dev/sda

During the installation I commit the full disk to Lubuntu.

But the installation summary informs me of an MSDOS partition table that also has space on the SSD.

That's my question.

I have a different problem with Intel ME and AMT, which could be related. I'm no longer able to boot after reinstallation with error messages relating to "mei".

---

### Post by Dennis N on 2019-09-29
You formatted the disk /dev/sda without creating partitions on it. The installer only installs the OS to partitions (like /dev/sda1), and in this case had to create the setup it needed.

---

### Post by CatKiller on 2019-09-29
> **ml9104 said:**
> During installation, I noticed that the installer creates an MSDOS partition table, although the entire disk is partitioned for Lubuntu and formated as ext4.
Why is this, please?

Thank You.

The MSDOS partition table doesn't have anything to do with DOS or Windows. It refers to the old [Master Boot Record](https://en.wikipedia.org/wiki/Master_boot_record) way of partitioning.

If you have that, it's because you booted your installation media in the old BIOS way, rather than the newer [UEFI](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) way: the install method used is based on the way the install media was booted, and a UEFI install will use a [GUID partition table](https://en.wikipedia.org/wiki/GUID_Partition_Table) instead. Note that GPT does include a stub MBR for some compatibility with machines that only understand MBR.

---

### Post by GhX6GZMB on 2019-09-29
> **CatKiller said:**
> The MSDOS partition table doesn't have anything to do with DOS or Windows. It refers to the old [Master Boot Record]("https://en.wikipedia.org/wiki/Master_boot_record") way of partitioning.

If you have that, it's because you booted your installation media in the old BIOS way, rather than the newer [UEFI]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface") way: the install method used is based on the way the install media was booted, and a UEFI install will use a [GUID partition table]("https://en.wikipedia.org/wiki/GUID_Partition_Table") instead. Note that GPT does include a stub MBR for some compatibility with machines that only understand MBR.

Thank You. This makes perfect sense, as it's a 10 years old HP/Compaq with BIOS.

---

