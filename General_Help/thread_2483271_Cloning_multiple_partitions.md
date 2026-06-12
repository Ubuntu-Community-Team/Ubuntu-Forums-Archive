---
title: "Cloning multiple partitions"
date: 2023-01-24
forum: General Help
---

### Post by dryw on 2023-01-24
[FONT=&amp]Hello Friends, nice to be here,[/FONT]

[FONT=&amp] I'm new to the subject, I need some advice on how to clone my Windows, [/FONT][FONT=&amp]currently[/FONT][FONT=&amp] in dual boot Windows - Linux, out of a SSD to an HDD.[/FONT]

[FONT=&amp] The final goal would be eventually to run it on a VM but also [/FONT][FONT=&amp]I [/FONT][FONT=&amp] just simply want to know more about backups. [/FONT]

[FONT=&amp] Here my situation 

```
[FONT=&amp]Disk /dev/nvme0n1: 465,76 GiB, 500107862016 bytes, 976773168 sectors[/FONT]
[FONT=&amp] Disk model: Samsung SSD 970 EVO Plus 500GB          [/FONT]
[FONT=&amp] Units: sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=&amp] Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=&amp] I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=&amp] Disklabel type: gpt[/FONT]
[FONT=&amp] Device             Start       End   Sectors   Size Type[/FONT]
[FONT=&amp] /dev/nvme0n1p1      2048   1085439   1083392   529M Windows recovery environment[/FONT]
[FONT=&amp] /dev/nvme0n1p2   1085440   1290239    204800   100M EFI System[/FONT]
[FONT=&amp] /dev/nvme0n1p3   1290240   1323007     32768    16M Microsoft reserved[/FONT]
[FONT=&amp] /dev/nvme0n1p4   1323008 489048063 487725056 232,6G Microsoft basic data[/FONT]
[FONT=&amp] /dev/nvme0n1p5 489048064 505733119  16685056     8G Linux swap[/FONT]
[FONT=&amp] /dev/nvme0n1p6 505733120 608133119 102400000  48,8G Linux filesystem[/FONT]
[FONT=&amp] /dev/nvme0n1p7 608133120 976773134 368640015 175,8G Linux filesystem[/FONT]
```[/FONT]
 
[FONT=&amp]I  made some homework. Let's see if I understood correctly the difference between an  image and a clone: both .VHD and .VDI (but also .ISO, .IMG, etc.) are  image files that can exist within a OS environment whereas a clone, not  being compressed, have to be recreated necessarily in its or[/FONT][FONT=&amp]iginal form in the drive. Have I got it right?[/FONT][FONT=&amp]
[/FONT]
[FONT=&amp] I've already tried to convert for fun p1, p2 and p4 (p3 was not visible) to a  .VDI (for VBox) using Disk2VHD but, naturally, I run on some issues with the boot.[/FONT][FONT=&amp] But these are images anyways.

[/FONT][FONT=&amp][FONT=&amp]I would like to focus on cloning. One  way I found, that I think may apply, is to dd the  section of the drive that goes from the start of p1 to the end of p4.[/FONT][/FONT]

Also, I seemed to understand that, in both imaging and cloning, is important to keep an eye on the boot section. Now, it is not clear to me if the boot section can be imagined/cloned together with the rest of the data or needs to be restored separately after. Same story for partition tables and boot loader. It seems that all of these need to be taken care of one by one either before of after cloning. I've read even to recreate the same partition order by importing the partition tables of the source and also making sure to maintain the same block size.

Any kind soul that can shed some clues about all this?

---

### Post by TheFu on 2023-01-24
Images are a terrible backup method.  Best to use file-based backups and begin your recovery with a fresh Ubuntu installation (10-15 minutes), then restore the files from your versioned, file, backups.  

Cloning can be performed at the whole disk level or partition level.  There are multiple methods. There are methods to copy the partition table layout from 1 disk to another.

Disks/SSDs come with different sized sectors. Usually sector sizes are either 512bytes or 4Kb.  When cloning between storage, going from same sector size to same sector size is fine.  Going from 512b to 4Kb is fine.  But going from 4Kb to 512b is NOT file.  You'll end up with misaligned sectors and for HDDs that will cause a huge performance hit.  Don't do it.  Also, if the cloning of the other sizes which should be possible isn't done correctly, then you'll have misaligned sectors again.  Best to avoid all that and use file-based mirroring - aka rsync.  rsync is one of the top 5 tools that all Linux users should know and use, however, it really isn't the best backup tool.  

There are lots of excellent versioned backup tools for Linux.

gdisk / sgdisk
gparted (can copy entire partitions and create file systems)
rsync
mkfs
are probably the tools you'll use for creating identical sized partitions.  rsync would be used to copy all the files.

If you use volume management, not just simple partitions, then there is much more flexibility, for a slight increase in complexity.  Volume management systems like LVM, ZFS, btrfs bring some enterprise capabilities do our home Linux systems. Most home users wouldn't use any of these, however.

If you insist on using cloning, please use ddrescue, not plain dd.

As for booting, the answer depends on whether UEFI controls booting or not.  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) has more than you'll care to know.  64-bit Windows required UEFI for booting for over a decade. MacOS has used it nearly 20 yrs.  It has been available on Linux since around 2012.  BTW, MSFT force some arbitrary things with their UEFI implementation, like using GPT partition tables.  Linux never cared.  GPT has been supported in either BIOS booting or UEFI since around 2010.

BTW, always use GPT for your disk partitions. Always.  There are so many reasons.

---

### Post by dryw on 2023-01-26
Thank you so much @TheFu, what an articulate and comprehensive answer!

>  If you insist on using cloning, please use ddrescue, not plain dd.

I heard great things about ddrescue especially for forensic. It does not have to be necessarily by cloning, but how else I can migrate, from the above SSD to another support, all relevant data about my Windows in a way that it can be booted the same way it does normally?

Also I am trying to find out more about what happened after I installed Linux. All I can say is since I installed Linux it seems GRUB took over Windows Boot Manager, but I don't know what happened at partition level, whether GRUB overwritten Windows Boot Manager or else.

Edit:

```
[FONT=monospace]nvme0n1   259:0    0 465,8G  0 disk  
nvme0n1p1 259:1    0   529M  0 part  
nvme0n1p2 259:2    0   100M  0 part /boot/efi 
nvme0n1p3 259:3    0    16M  0 part  
nvme0n1p4 259:4    0 232,6G  0 part  
nvme0n1p5 259:5    0     8G  0 part [SWAP] 
nvme0n1p6 259:6    0  48,8G  0 part / 
nvme0n1p7 259:7    0 175,8G  0 part
[/FONT]
```

It appears the the bootloader is in p2

---

### Post by TheFu on 2023-01-26
Read that link already provided about UEFI.  There aren't any "boot sectors" anymore.  What Windows does is far, far, outside my knowledge.  Use a Windows tool for that.

---

### Post by tea for one on 2023-01-26
> **dryw said:**
> Also I am trying to find out more about what happened after I installed Linux. All I can say is since I installed Linux it seems GRUB took over Windows Boot Manager, but I don't know what happened at partition level, whether GRUB overwritten Windows Boot Manager or else.
According to the info in post 1, you have an EFI system with GPT, this is the modern way.
Now, Grub is the boot manager but it has not overwritten or eliminated the Windows Boot Manager.
Grub has only added a menu entry for Windows.

When you power on the PC, can you access the one-time boot menu with the dedicated key (F10 or F12 or similar)?
Do you see a list of disk drives?
Or a list of Operating Systems and disk drives?

It very much depends on the PC vendor's configuration of the UEFI firmware?

---

### Post by dryw on 2023-01-26
[FONT=&amp]>  Now, Grub is the boot manager but it has not overwritten or eliminated the Windows Boot Manager.[/FONT]

[FONT=&amp] I agree. Based on my recent findings if Windows Boot Manager gets overwritten or corrupted Windows doesn't boot, while mine boots just fine.[/FONT]

 
[FONT=&amp]```
Grub has only added a menu entry for Windows
```[/FONT]

[FONT=&amp]Right! Windows Boot Manager is fine. It is set as boot option 2 in the bios settings of my motherboard while GRUB is 1. I tried to reverse the two and Windows came up at once. I wasn't presented with the choice menu Windows - Linux though. Not very democratic...

Anyways, so at least I know [/FONT]*[FONT=monospace]nvme0n1p2[/FONT]*[FONT=monospace] [FONT=arial]is a necessary "piece of the puzzle" to have a replicable clone OS.
[/FONT]
[/FONT][FONT=monospace][FONT=arial]It seems all I am left is choosing which tool to use to do the job. Is it? Or should I take care of the partition tables first?[/FONT][/FONT]

---

### Post by yancek on 2023-01-27
If you boot Linux and look at the /boot/efi/EFI directory, you should see a directory named Microsoft which contains the windows EFI boot files as well as a directory named ubuntu which contains the Ubuntu EFI boot files.  This means on an EFI install, the boot files for different systems will be in separate directories and they will not be overwritten by the installation of a bootloader for another OS.  With Legacy install to the MBR, boot code was always overwritten.  Grub will chainload a windows EFI install from a Linux EFI install but a default windows will not boot any Linux.  There is a convoluted process to boot a Legacy install of Linux from a Legacy install of windows as well as third party software called EasyBCD which would do the same.  I don't know if this is possible with an EFI install.

If you want to clone an entire rive, clonezilla is software that was designed for that purpose.

---

### Post by TheFu on 2023-01-27
> **dryw said:**
> It seems all I am left is choosing which tool to use to do the job. Is it? Or should I take care of the partition tables first?

If the old disk is mostly full, say 90% or more, I'd use 'ddrescue' to clone everything at the whole device from the old to the new.  Because this clones everything, UUIDs will be identical, so the two storage devices cannot be used in the same machine.  After the cloning and everything is working with the new storage, I'd connect the old storage to some other systems, running linux, and force the UUIDs for the disk, partitions and file systems to be changed. I'd probably wait a week to do this, to ensure the "new" storage is working fine.  The actual values of the UUIDs aren't important, just that they don't conflict.

If the old storage were less full, 
* I'd use 'sudo sgdisk' to copy the existing partition table. There are examples online.  I just remember that the source and target are in odd places in the command.  I'd do any partition resizing using 'gparted' at this point, BEFORE any data is on the drive, so it will be fast.
* I'd use 'sudo mkfs' to create the new file systems in each partition.  ext4.  I suppose the FAT32 partition needs to be created too.
* Then I'd use 'sudo rsync -avz {source} {target}' to mirror the contents for each partition from the old into the new.  This is file-based, so it won't copy empty space and if it gets interrupted, re-running it will effectively pick up where it left off.
* This process will generate different UUIDs for everything, so the /etc/fstab will need to be updated where the old UUIDs are replaced with the new ones.  'blkid' will show the UUID to device mapping. When you know what you are doing, this is a 30 second fix using select/paste from any GUI in Linux and 'sudoedit' to modify the fstab file. If you are typing anything, then you are doing it the hard way.

Disconnect the old storage and reboot. With EFI booting, the /boot/efi/EFI area will be seen, and menu created for boot choices.
Using ddrescue seems easier (all byte for byte copy tools), but because it brings everything over, including fragmented junk, there are reasons to prefer the rsync method which will end with a de-fragmented file system.

As for moving Windows stuff, I can only say to use Windows tools for that, or use ddrescue at the partition level, not the whole drive level.  An understanding of linux storage device naming is the key to getting these device names correct.  Think I tried to explain them a few months ago.

To use any of these tools, you'll need to ensure the source storage isn't being used at all to avoid risking corruption of the files.  That means booting off alternate media.  I'd use the Ubuntu ISO flash drive used to install the OS. Keep one of those around.  They are also handy for online banking in a secure, locked, environment.  Anyway, boot into the "Try Ubuntu" setup to get a full desktop Ubuntu running from the flash drive, install the desired tools, ddrescue or the other set. These are only installed while this Try Ubuntu is running. At reboot, they are gone.  You could create a USB installer version with some permanent storage, but this is less useful than it might seem and does add risks for infection from malware, which is a key reason why you DO NOT want the overlay, but just want a simple ISO to be used.  You'll need to flash boot storage regardless.  'Ventoy' is a handy way to have multiple ISO tools/OSes on a single flash drive.  It is also useful to have them for troubleshooting boot issues in 6, 12, 36 months until it is time to install a new OS (which it can be used to accomplish too).

I always found clonezilla to be overly complex. Perhaps I'm just stupid.  ddrescue is simple.  I've also used fsarchiver for partitions, but it seems to know that NTFS is a problem, so they don't recommend using it for NTFS storage.

---

### Post by C.S.Cameron on 2023-01-29
**For what it is worth, the method I use to convert .vdi to .img:**

Virtual Machine: 

Convert .vdi file to .img file that can be flashed to bootable USB.

- Open VirtualBox

- cd to folder that contains [file name].vdi and run:

```
VBoxManage clonemedium --format RAW [file name].vdi [file name].img
```

To convert .img to .vdi transpose .vdi and .img in the above.

---

### Post by TheFu on 2023-01-29
qemu-img can convert almost any file-based virtual storage to almost any other file-based virtual storage.  The top of the qemu-img manpage
```

QEMU-IMG.1(1)                                                           QEMU-IMG.1(1)

NAME
       qemu-img - QEMU disk image utility

SYNOPSIS
       qemu-img [standard options] command [command options]

DESCRIPTION
       qemu-img allows you to create, convert and modify images offline. It can
       handle all image formats supported by QEMU.

       Warning: Never use qemu-img to modify images in use by a running virtual
       machine or any other process; this may destroy the image. Also, be aware that
       querying an image that is being modified by another process may encounter
       inconsistent state.
...

```
There are about 10 pgs of explanations for the options, but 
```
sudo qemu-img convert input.vdi output.img
```
The manpage says the output format is guess by the filename, but the -O parameter can be used to override it.

Supported formats on my system are:
```
Supported formats: blkdebug blkreplay blkverify bochs cloop dmg file ftp ftps host_cdrom host_device http https iscsi iser 
  luks nbd null-aio null-co parallels qcow qcow2 qed quorum raw rbd replication sheepdog throttle vdi vhdx vmdk vpc vvfat
```
Yours are probably a little different.  As seen, the list is extensive.

---

### Post by dryw on 2023-01-29
> ...they will not be overwritten by the installation of a bootloader for  another OS.  With Legacy install to the MBR, boot code was always  overwritten.
Thanks @[**yancek**]("https://ubuntuforums.org/member.php?u=1928724")**, **yes, just my worries from old info read around. There is still a lot about MBRs online




> If the old disk is mostly full, say...
Wow @[**TheFu **]("https://ubuntuforums.org/member.php?u=1037685") this truly is one hell of a guide. Thanks also for the extra info. Very exited!!

So, copying partition tables is a necessary step after all. 
By copying them to the target drive do we get already an exact replica of the source (same size, etc.) but empty?
Will a corrupted partition table file cause access issues or brick a drive?

My partitions are half empty therefore I do not thing I will use ddrescue.

>   I'd do any partition resizing using 'gparted' at this point, BEFORE any data is on the drive
So long I don't make them smaller then the source or smaller then the actual data (no empty space if I use rsync). Right?

>  I'd use 'sudo mkfs' to create the new file systems in each partition.   ext4.  I suppose the FAT32 partition needs to be created too.
If in my case I have to boot Windows I assume file system is the very same (ntfs) from the source, right?

> Then I'd use 'sudo rsync -avz {source} {target}' to mirror the contents for each partition from the old into the new.
This will be just allocating all data nice and defragged in the target drive?

> This process will generate different UUIDs
This does not apply to Windows, right?

Seems a bit laborious but efficient, especially rsync tidying up all data leaving the empty space behind, fantastic!

Okay, how about as a lazy periodically backpacking method, I wanted to clone, with one quick command or one uninterrupted copying process, the following:

```
[FONT=monospace]
nvme0n1p1 259:1    0   529M  0 part  
[/FONT][FONT=monospace]nvme0n1p2 259:2    0   100M  0 part /boot/efi 
nvme0n1p3 259:3    0    16M  0 part  
nvme0n1p4 259:4    0 232,6G  0 part[/FONT]
```

which should be the part of the SSD that contains all relevant data to run Windows.
What would the right way be?




```
VBoxManage clonemedium --format RAW [file name].vdi [file name].img
```

To convert my .[FONT=&amp]VHDX to .VDI if I remember correctly I used:

[/FONT]```
 VBoxManage convertfromraw /path/to/VHDX /path/to/new/VDI --format VDI
```[FONT=&amp]

I had no idea what that actually do then I have no idea now :P The .VDI I got did not boot.
Another reason why I want to make a clone out of Windows is to then lighten it in a way it can run as smoothy as possible on the VM. Something I do not want to do on the original in the SSD.  

Do you guys actually have any idea why I couldn't boot the .VDI in Vbox? 

Here is what happen when I launch 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291666&stc=1[/IMG] [/FONT]

---

