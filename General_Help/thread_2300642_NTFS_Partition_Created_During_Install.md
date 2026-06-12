---
title: "NTFS Partition Created During Install"
date: 2015-10-27
forum: General Help
---

### Post by spode2 on 2015-10-27
I installed Lubuntu onto a Windows 7 PC by adding a 120GB SSD for Lubuntu and choosing which OS to boot to from the GRUB menu.

When I installed Lubuntu, I followed the defaults when it came to partitioning the new drive and for some reason the drive ended up with half of it formatted to NTFS and labelled as partition 1. The other half is an extended partition 2 containing the file system in partition 5 and swap file in partition 6.

I would like to delete the NTFS partition and use gparted to add the unused space to the file system partition. Do I need to leave some NTFS space for any reason and can I just add the partition 1 space to partition 2?

Will partition 2 be renamed when I delete partition 1?

---

### Post by Vladlenin5000 on 2015-10-27
No, you don't need any NTFS partition if you're only running Ubuntu and yes, you can remove it, move the Ubuntu partition(s) to the left and expand to use the whole drive. Please note this operation is usually safe but by no means risk free.
Why that happened in the first place? Because of the side by side option you selected during installation, the default option whenever another OS is found already installed.

---

### Post by yancek on 2015-10-27
Another option is to simply use GParted from the Lubuntu installation media and format the ntfs partition to a Linux filesystem such as ext4.  Then you would not have to move any data and risk an unbootable machine.  Create a mount point for the partition and put an appropriate entry in your /etc/fstab file.

---

### Post by spode2 on 2015-10-27
Thanks for the replies.

The file system and swap files are "contained" in the extended partition 2. If I use gparted to extend this to fill the disk, will it remain an expanded partition, or will it become a primary partition? I might want to make it directly bootable one day and I have read that you can only boot from a primary partition.

---

### Post by oldfred on 2015-10-27
May be best to see what partition is? I did not think it was even possible to create a NTFS partition directly from installer, unless Lubuntu has changed.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Windows only boots from a primary partition with BIOS/MBR. But Linux does not care and can boot from any partition. With two drives best to keep Windows boot loader on Windows drive and grub boot loader on Ubuntu drive. And set BIOS to boot Ubuntu drive. But grub only boots working Windows and you sometimes may have to try to boot Windows directly or better to have a Windows repair CD or flash drive.

---

### Post by spode2 on 2015-10-27
Oldfred,

Yes, now I think about it the new disk was probably factory formatted and Lubuntu just defaulted to using half of it. I have deleted the NTFS half now, so it's empty space. I'll have a play with gparted and see if I feel confident enough to expand the file system partition into it.

Thanks again for the help and advice.

---

### Post by yancek on 2015-10-27
> The file system and swap files are "contained" in the extended partition  2. If I use gparted to extend this to fill the disk, will it remain an  expanded partition, or will it become a primary partition? 

Is or was the ntfs partition at the beginning of the disk?  If it was, much simpler to just create another partition with a Linux filesystem rather than messing around with resizing the partitions which will move files including boot files and if something goes wrong, you will have an unbootable machine.  An Extended partition is a primary partition, it just doesn't contain data but is a container for logical partitions.

> I might want to make it directly bootable one day and I have read that you can only boot from a primary partition. 		

You can boot any Linux system on a logical partition.  If you have windows, you must have the boot files on a primary partition marked as active but the rest of the system files can be on a logical partition.

---

### Post by spode2 on 2015-10-27
Yancek,

Thanks for the explanation. You are probably right. I will not do anything which is high risk.

---

