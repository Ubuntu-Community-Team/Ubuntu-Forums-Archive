---
title: "Going all ubuntu 12.04"
date: 2012-11-22
forum: General Help
---

### Post by larswebb on 2012-11-22
Hi everyone,

  After dual booting ubuntu 11.04 and Windows 7 for quite a while I have decided to go all ubuntu12.04. I currently have 2 hard drives, one 250g sata with W7 and ubuntu11.04 dual boot and one 750g sata data drive. I removed the 250 drive and replaced it with a new 120 ssd sata. I put the ubuntu 12.04 disk in and booted to it. I chose to install ubuntu but it stated that W7 was there and asked if I wanted to replace it or install along side of it. I'm confused... I removed the drive with W7 on it. Am I doing something wrong?

Regards,
Larry

Ubuntu11.04,W7 Dual boot
Asus P7p55D
250g Seagate sata
750g Seagate sata
4 gig Kingston ram

Larry

---

### Post by ajgreeny on 2012-11-22
Can we see the output of ```
sudo fdisk -l
``` with the W7 disk removed please.

---

### Post by efflandt on 2012-11-23
Are you installing from iso on USB with persistent data?  I had strange things happen after installing 64-bit 12.04 to my desktop and then trying to use the same USB stick to install to a laptop.  It seemed to remember some things that I configured for the desktop skipping a menu and choking with errors trying to copy settings from a drive that did not exist on the laptop.

I used Startup Disk Creator to rewrite the image to the USB still and then all the menus appeared and worked, but it kept hanging indefinitely (hours) with no errors after writing/downloading/writing about 95% of the system to disk.  Although, that may have been some other issue.  I finally used the 64-bit 12.04 alternate iso for the laptop and the system booted fine.

---

### Post by larswebb on 2012-11-23
I am installing from 12.04 ISO I  downloaded from ubuntu. I had to re-istall the 250g drive to use this  machine.  I am going to try again and use the live CD to run f disk -l  as recommended by [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") 
 I did notice that my data drive has a boot folder  in it. I seem to remember reading somewhere that putting the boot  folder on a separate drive was a good idea. I think I remember doing  that.

---

### Post by larswebb on 2012-11-23
results-

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x164ba72e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       16126  1465144064   732563969+   f  W95 Ext'd (LBA)
/dev/sdb5           16189  1465144064   732563938    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 64 MB, 64487424 bytes
4 heads, 32 sectors/track, 984 cylinders, total 125952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5bfd618d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32      125823       62896    6  FAT16
ubuntu@ubuntu:~$

---

### Post by larswebb on 2012-11-23
I tried renaming that boot folder on the data drive. I was able to install ok but it wouldn't boot. Grub rescue error. 

Here are the updated results


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004000c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   226058239   113028096   83  Linux
/dev/sda2       226060286   234440703     4190209    5  Extended
/dev/sda5       226060288   234440703     4190208   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x164ba72e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       16126  1465144064   732563969+   f  W95 Ext'd (LBA)
/dev/sdb5           16189  1465144064   732563938    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 64 MB, 64487424 bytes
4 heads, 32 sectors/track, 984 cylinders, total 125952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5bfd618d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32      125823       62896    6  FAT16
ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-11-23
Best to see details of what is where.

       
Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    Have you changed BIOS to AHCI and made some settings changes to SSD?

Lots of detail on SSD.
       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by larswebb on 2012-11-24
I used boot repair and it it worked well. I am up and running 12.04 all though I don't like it and have already experienced problems updating and running the software center.  But that&#8217;s another thread if I can't figure it out.

Thank you for your assistance
I will mark this solved

---

