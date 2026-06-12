---
title: "Ubuntu installer cannot find Windows 7 at all."
date: 2015-08-07
forum: General Help
---

### Post by felix28 on 2015-08-07
(This is my first time using these forums, so apologies if this is in the wrong place or anything like that)

So, by a friends suggestion, I tried to install Ubuntu 14.04 the other day, in a dual-boot setup.

I put it on a bootable flash-drive, booted it with flash drive, and everything worked fine. Some driver issues but nothing that looked like it couldn't be fixed.

After messing with it from the live USB for a while, I clicked the installer. Everything worked fine. WiFi worked. It had enough space. Everything seemed normal.

Once I got to the partitioning bit, it said that it couldn't detect any other operating systems. For some background information, I have a 500 gigabyte drive which Windows 7 is installed on, and a 1 terabyte drive with games and files.

After going to the "Something Else" menu for manual partitioning, it got even weirder. It could see the 1 terabyte drive, with all the correct partitions and everything. But the 500 gigabyte said that it was 100% completely unpartitioned. Entirely free space.

Back in Windows, I did run chkdsk /r and I defragmented the drive. Going back into Linux, nothing changed.

To make the matter even stranger, I can mount the Windows drive from the file manager, and view all files inside. But the installer still says that it can't detect any partitions on the drive.


TL;DR: Ubuntu installer can't see Windows 7, or any partitions at all on the drive which Windows 7 is on.

---

### Post by yancek on 2015-08-07
The Ubuntu install medium has the partition manager GParted on it.  Boot it and open a terminal and just type:  gparted and hit the Enter key.  It should show your drives/partitions.  How many partitions do you have on the 500GB drive?  Did you do an mdt checksum on the Ubuntu iso download before putting it on the flash drive?

---

### Post by oldfred on 2015-08-07
Almost every Windows 7 system used all 4 primary partitions with MBR(msdos). So only alternative with auto install is erase drive. You need to remove one partition and usually the easiest are the vendor utilities which is small and easily backed up or the vendor restore which usually can be copied/installed to a DVD set or flash drive.

Post this from terminal in Live installer:
sudo parted -l

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by felix28 on 2015-08-08
When I started up GParted, it said:

 "/dev/sdb contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partiton table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table?"

/dev/sdb is the 500 gigabyte drive, as far as I'm aware.

I clicked "Yes", and GParted said that the 500 gigabyte drive (/dev/sdb) was completely 100% unpartitioned. Not a single partition. Completely empty.

I have booted the Ubuntu installer with and without UEFI and the same thing happens both ways, so I don't think it's a problem with UEFI either.

---

### Post by oldfred on 2015-08-08
Windows converts gpt  drives to MBR(msdos) but does it incorrectly. It creates the MBR partition table but leaves the gpt backup partition table. So Linux tools see both, and assume you need to erase entire drive.
You can remove backup gpt partition data with fixparts.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But if drive is only Ubuntu, may be better as gpt. Ubuntu can boot in BIOS mode or UEFI mode from gpt drives. With UEFI you have to have the ESP -efi system partition. And with bios you need a tiny unformatted 1 or 2MB bios_grub partition on gpt drives.
But you need to install Ubuntu in same boot mode either BIOS or UEFI as Windows to easily dual boot. 
And Windows only boots from gpt partitioned drives with UEFI.
And Windows only boots from MBR partitioned drives with BIOS.

I now partition all new drives with gpt as I do not install Windows and have both an efi & bios_grub partition. Then drive can be used on older system now in BIOS and newer system later in UEFI without having to totally erase & repartition. There are tools to convert from MBR to gpt but never attempted that.

       
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

