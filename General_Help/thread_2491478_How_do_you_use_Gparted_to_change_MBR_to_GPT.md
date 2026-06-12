---
title: "How do you use Gparted to change MBR to GPT"
date: 2023-10-10
forum: General Help
---

### Post by jacatone on 2023-10-10
Anyone know how to explain this process in simple turns?

---

### Post by oldfred on 2023-10-10
Using gparted will totally erase entire drive. Be sure to have good backups of any data on drive you want to keep.

In menu options at top.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

You can use gdisk to convert, but have to manually reinstall grub, update fstab & make other changes. Best to only use on data only drives.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Screenshot from older version of gparted, but basically same now.

---

### Post by MAFoElffen on 2023-10-10
Risky... Do you have good backups? Is it your root drive or a data drive? (such as a separate mounted  /home)

EDIT: Sniped... LOL

So I'll just add the rest... 

GPT is going to erase the drive anyways, so I prefer to back up the data that is on that drive to another... Then to manually convert it with a fresh GPT partition table and create new partitions. This may take some modifications in an extra leading partition or two. 

Depending on the target computer and how it boots, and it it was a root drive that it needs to boot from... 

If a root drive: 
Boot from an installer LiveUSB, close to the versio of the installed system. Drive partitions can't be altered if mounted... 

If the computer boots from BIOS, then in GParted create a new partition, with about 1MiB in front of it, about 5MiB in size. Leave unformated. After you select apply, then right click on it > Select flags > set to bios_boot. Save. Grub2 needs ths special partition to boot as Legacy from GPT drives...

 If it boots as UEFI or converting to boot in tha mode, then the first partition needs to be about 750 MiB to 1GB, formatted as FAT32. After you select apply. Then right click on it > flags > ESP, boot. Save.

Note, If Legacy Boot, you can always add both of those partitions, and have them both there, to be able to install it in a UEFI mode booted computer in the future... with only having to reinstall grub for that boot mode.

If root drive or data drive: 
Add all your other partitions. Apply. Restore your data to those partitions.

If a root drive additional:
Mount the root partitions. Mount the temp filesystem. chroot into the installed system. Remount the fstab. Reinstall grub based on the boot mode. Reboot and test.

Then restore the data on each partition...

---

### Post by TheFu on 2023-10-10
Perhaps something like **gdisk** would be a better choice?  With simple partitions, I think it can handle the conversion, but not for every possible way that partitions and disks can be setup.  

From the manpage:
```
DESCRIPTION
       GPT  fdisk  (aka gdisk) is a text-mode menu-driven program for creation and manipula&#8208;
       tion of partition tables. It will automatically  convert  an  old-style  Master  Boot
       Record (MBR) partition table or BSD disklabel stored without an MBR carrier partition
       to the newer Globally Unique Identifier (GUID) Partition Table (GPT) format, or  will
       load  a  GUID partition table. When used with the -l command-line option, the program
       displays the current partition table and then exits.
```

I wouldn't trust any partitioning tool to handle the conversion without first having backups for everything I don't want to lose AND knowing how to restore those.

These conversions don't magically address advanced volume manager needs or modify the /etc/fstab file, if any modification is required. The system administrator is expected to handle those manually.

---

