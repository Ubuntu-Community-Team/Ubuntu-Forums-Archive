---
title: "Format HP Laptop for Ubuntu"
date: 2021-10-11
forum: General Help
---

### Post by webmanoffesto on 2021-10-11
I have an HP cn17053cl
And I want to format it for Ubuntu. 
In KDE Partition Manager I see
Toshiba 931 GiB
/dev/sda1 fat32, System, EFI system partition, 260 MiB
/dev/sda2 unkown, Microsoft reserved partition, 16 MiB
/dev/sda3, ntfs, Windows, Basic data partition, 930 GiB
/dev/sda4, ntfs, Windows_RE_tools, Basic data partition, 530 MiB

To partition this for Ubuntu (Lubuntu right now, lately that works best for me as a bootable flash drive)
I guess I will keep the EFI system partition. I've struggled with the EFI system partition and Legacy boot. EFI on a GPT disk, or whatever.

Would you recommend that I delete 
/dev/sda2 unkown, Microsoft reserved partition, 16 MiB
/dev/sda3, ntfs, Windows, Basic data partition, 930 GiB
/dev/sda4, ntfs, Windows_RE_tools, Basic data partition, 530 MiB

and create a root directory for Lubuntu and a Home directory for all my files?

This is not dual boot.

---

### Post by grahammechanical on 2021-10-12
> This is not dual boot.

That will make all the difference. You have no need for anything to do with Microsoft and Windows. But are you sure? You will still have some Windows boot files left in /dev/sda1. The EFI system partition. They can be deleted. And it is in that partition that the Lubuntu installer will put some boot files for Lubuntu. There is room in that EFI partition for both Windows EFI and Ubuntu EFI boot files, anyway.

GPT is better than the MBR partition table. It is good to have a root partition and a home partition. You choose the Something Else option to direct the installer to use those two partition. The file system (format) on both should be Ext4. If there is a need to re-install it will be safe to mark the root partition to be formatted but do not mark the home partition for format as that will wipe out all the user configuration files in the /home folder/directory and the data in the Documents, Downloads, Music and Videos directories/folders.

I have a third partition formatted to Ext4. I call it Data partition. It is where I store/backup my useful documents and files. You can create this at the same time as you create the other partitions. But it does not get assigned during the install process. The file manager will still access it and that action "mounts" it. Also it is possible to edit a configuration file so that it is automatically mounted at boot time. That is another question for this forum. First things first. Install Lubuntu!

Do not forget to run the Lubuntu ISO image USB stick in UEFI mode and not legacy mode. 

Regards

---

### Post by tea for one on 2021-10-12
> **grahammechanical said:**
> Do not forget to run the Lubuntu ISO image USB stick in UEFI mode and not legacy mode.
This is a good reminder.

When you have booted into a live Lubuntu session, you can double-check if you are in UEFI mode by entering this in a terminal
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

> GPT is better than the MBR partition table.
Yes, GPT is the modern way.
GPT (partition table) is a user choice created using your partition manager.
It may not be the default.

---

### Post by GhX6GZMB on 2021-10-12
Let the Lubuntu installer do the formatting. Plan your partitions first and select manual partioning. File system should be ext4, and tick the "format" option for each partition.
The Lubuntu installer (Calamares) is really good.

---

