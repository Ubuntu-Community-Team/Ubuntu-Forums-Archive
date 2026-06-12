---
title: "Moving day part 2 - BIOS/MBR to GPT and UEFI"
date: 2017-06-06
forum: General Help
---

### Post by Kris_M on 2017-06-06
Okay, I survived yesterday. SSD now looks like pic below.

Ubuntu is at start of SSD 
BIOS settings mobo set to non-win8(bios)
boot is bios
SSD is MBR
ie bios system.
mobo is a year or 2 old and bios on it is latest so quite current though not bleeding edge.
I single boot.  win is gone.

I do not know the order to do things.
# change setting in mobo bios.
# change partition from MBR to GPT w/o re-installing (I have Clonezilla image to restore but don't know if I can restore image taken from MBR to GPT drive)
# change grub to boot GPT system
# change Ubuntu to GPT
in some order.
I have heard that if I change the SSD to GPT I won't be able to boot it - Will Boot-repair fix that?

I have both Boot-Repair and Rescatux (separately) on uefi bootable thumbdrives.
I have a Clonezilla image if everything goes bust.
I have a separate laptop[ that I can use to communicate with forum while working through this.

THANKS!!!
oldfred now, finally I beg your knowledge!- now reading your UEFI installing tips thread.

STARTING PROCESS:
mobo bios is now fast boot disa
windows 8
CSM support always
Storage boot option UEFI first  (I now notice short pause in boot, and short pause before Ubuntu, but boots fine.

```
kris@kris-Z97X-UD3H:~$ sudo parted -l[sudo] password for kris: 
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 3      1049kB  250GB  250GB   extended                  lba
 5      2097kB  121GB  121GB   logical   ext4
 6      121GB   125GB  4194MB  logical   linux-swap(v1)

Model: ATA TOSHIBA MK6465GS (scsi)
Disk /dev/sdb: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      8225kB  640GB   640GB   extended               lba
 6      9437kB  32.5GB  32.5GB  logical   ntfs
 7      32.5GB  65.0GB  32.5GB  logical   ntfs
 5      106GB   640GB   534GB   logical   ntfs

Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs
kris@kris-Z97X-UD3H:~$ 

```

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=14f8bc13-3090-4bbf-96c0-1f30ea3ec99a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=cd961766-73c5-4de7-b54d-3f1ac2ca0a84 none            swap    sw              0       0
# UUID=bfeeb626-5855-44d9-b91d-2c7a1ac72e4d /work ext4 defaults,noatime 0 2
UUID=01D195FDD65B0990 /media/E ntfs-3g defaults,noatime,windows_names,locale=en_US.utf8 0 0
```

---

### Post by oldfred on 2017-06-06
Putting me in title does not help. I will remove it, so others may also respond.
Occasionally I will acknowledge a PM.
But I am usually around, and any  thread title with boot issues, grub or similar I at least look at.

I only changed to gpt when I totally erased an old 160GB drive that had 32 bit Ubuntu and was an older copy. I was installing a new 64 bit version.
I repartitioned/reformatted & installed Ubuntu. Some original issues as gpt was fairly new, found out I had to have bios_grub partition. And it originally did not like to boot Windows XP that was MBR from grub that was gpt, long since fixed.

I do prefer to have both ESP - EFI system partition and bios_grub as first two partitions. UEFI suggests ESP be first, but even most Windows installs have it second or even third, but still somewhat close to start of drive. UEFI has to read it, so should not be too far into the new multiple TB drives, but have seen users put it near end of smaller SSDs. You do not need an ESP unless you also want to experiment with UEFI. And then UEFI/BIOS settings would be requried.

Grub say bios_grub can be anywhere on drive, so easy to just slightly shrink any partition.

       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 
    

You cannot restore a MBR image to gpt.
I use rsync and have copied data from MBR to gpt.
Gpt has more internal structures for reliability including GUID in partition which must match both partition table & backup partition table. That is why you can only use dd to copy an entire gpt drive not a partition without major issues.

If  you only want BIOS boot, you can convert in place (still have backups) and add a 1 or 2MB bios_grub unformatted partition with bios_grub flag is using gparted. If using gdisk it is code ef02. Grub stores core.img as raw data in the bios_grub partition. It only needs to be 1 or 2MB and that is only for compatibility with new 4K drives, actual space used by core.img is smaller.

Rod Smith created gdisk and is most knowledgeable on gpt. Gdisk was the equivalent to fdisk. Only the newer fdisk in 16.04 finally supports gpt drives. His rodbooks site has loads of useful info.
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
Be sure to read all the cavaets. 
If you backup partition table, you can also then restore it if necessary.
sudo sfdisk -d /dev/sda > PT_sda.txt 


You will need to reinstall grub, either manually or with Boot-Repair, after you create to bios_grub partition. The core.img that was in sectors after MBR is gone as gpt's protective MBR has no space after it. In BIOS/MBR there was a lot of space after MBR but before first partition and that was where core.img goes. But Windows also used same space often creating conflicts.

For BIOS boot,  you should not need any changes in UEFI/BIOS as already set to boot in BIOS mode. 

The reinstall of grub will change settings from (hd0,msdos1) to (hd0,gpt1) for example in grub.cfg. I have used (hd0,1) and it still works.
Not other changes to Ubuntu should be requried.
 
So use gdisk to convert with its save command.

 sudo gdisk /dev/sda
Command (? for help):
 launch gdisk, then type x advanced options, then type e backup to end of drive, then type w to save your changes or q to quit without changes if issues.
You may have to slightly shrink last partition if not room for backup gpt partition table at end of drive.

Then create new bios_grub partition anywhere on drive. Unformatted 1MB with bios_grub flag. I have only seen 2MB required with some other formats like btrfs where core gets very large.

Then reinstall grub2 with Boot-Repair's advanced options. Choose the full reinstall option.

Once you get that working, and if you want to experiment with UEFI post back.

---

### Post by Kris_M on 2017-06-06
Many thanks oldfred for your ideas.

STEP 1:
mobo bios changed to:
fast boot "disa"
"windows 8"
CSM support "always"
Storage boot option UEFI first (I now notice short pause in boot, and short pause before Ubuntu, but boots fine.
[B]_Ubuntu booted fine!_
[/B]
STEP 2:
Conversion:
Gparted offline resize sda5 from 120gb to _**50gb**_ to make following processes easier.
Clonezilla backup sda5 _part_, _**AND**_ sda _whole disk_ (just in case)
Gparted offline:
- create GPT partition table on sda (destroys everything).
- create _**51GB**_ ext4 (sda1) with small space in front.
- create unformatted 10MB in small space, flagged as bios-grub. (gparted shows a diamond yellow exclamation point - ignore) (thanks oldfred!)
- greate a 4GB swap with 62GB or so space in front of it.
Clonezilla restore part saved above to new sda1 partition (I sized it larger because I don't know how/if Clonezilla deals with smaller targets)
(booted offline gparted again just to look at it and check)
Rescatux - chose easy and picked sda1(clearly labeled as Ubuntu 16.04), sda, ordered sda,sdb,sdc,sde, ok,ok,etc, etc

AS expected, reboot to Ubuntu was slow after notification around ramdisk because of fstab and swap - 2 min or so.
Update fstab with correct UUID for swap: -  sudo blkid / sudo gedit /etc/fstab
Reboot and done.
Quite simple, actually, thanks to Clonezilla.

Thanks to all who looked in!

---

### Post by oldfred on 2017-06-06
If you want to experiment with UEFI you now have space between bios_grub and sda1.
If you make a FAT32 formatted partition and add the boot flag then it is an ESP - efi system partition.
And then you can install grub-efi-amd64 for UEFI boot and uninstall grub-pc for BIOS boot.

Some UEFI have "Windows" and Other. If Windows is on, then that is UEFI secure boot. As often fine print somewhere says if installing Windows 7 you must use "Other" as it does not support Secure Boot. BIOS/CSM/Legacy is always Secure Boot off.

I think sudodus tried to do both on a flash drive, and it works for a while.
Its  just updates may get out of sync with version of grub installed/booted. Then  other mode does not work.

 Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode 16.04
[http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13468260#post13468260)
Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)

I typically like to have ESP & bios_grub first and swap last as those three partitions I will never change or expect never to change. Then all space in between and be adjusted without those partitions being in the way. With 17.10 we now will not get swap partition unless we already have it.

---

### Post by Kris_M on 2017-06-06
EDIT - Okay, if I create that 256MB partition as fat32 flagged esp,boot, my mobo bios does indeed see it
It doesn't see anything bootable on it (when I switch CSM off).
Can I convert Ubuntu or do I have to rebuild it?
got this in another thread.

---

### Post by oldfred on 2017-06-06
You have to install the version of grub for UEFI boot.
That is grub-efi-amd64. 
Since booting in BIOS mode now, you have grub-pc.
 But you need the full uninstall/reinstall if using Boot-Repair.
I think since you can boot, you just can from command line uninstall grub-pc and install grub-efi-amd64.

---

### Post by Kris_M on 2017-06-07
yep - replied in the other thread - will use that one.

---

