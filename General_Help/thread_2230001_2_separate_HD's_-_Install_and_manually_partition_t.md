---
title: "2 separate HD's - Install and manually partition the Ubuntu Drive? w/Win HD Unplugged"
date: 2014-06-16
forum: General Help
---

### Post by 777funk on 2014-06-16
I'm having a heck of a time installing Ubuntu and getting it to boot. I've been unplugging the Win HD.

I used the stock ubuntu installer partitioning (AUTO) and it will boot. But if I manually partition (what I'd like to do), it will not boot. 

What could the problem be?

I'd like to have Ubuntu not touch anything (even the factory Windows MBR) on the original HDD.

---

### Post by Bashing-om on 2014-06-16
777funk; Humm ..

Windows on that 1st hard drive .. Are we talking Windows 7 (late 7 or Windows 8 ? ) such that we must consider that the booting is EFI rather than MBR ?
Show us what we are working with. Post back the outputs - between code tags - of terminal commands :
```

sudo fdisk -lu ##for MBR booting##
sudo gdisk -l /dev/sda ##for EFI booting##
sudo gdisk -l /dev/sdb ##for EFI booting##
sudo parted -l
sudo blkid

```
And we will see what it will take to make this work.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by 777funk on 2014-06-16
This is Win7 Pro on the first drive. It's interesting because I just installed Ubuntu on Drive sdb and put the boot loader on that drive (selected sdb for bootloader) and even when I manually boot (from BIOS) to the sdb drive, it's a no go.

OK just logged into a LiveInstallerCD and got this for -lu:
```
xubuntu@xubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdf67eae9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    48383999    24088576   1b  Hidden W95 FAT32
/dev/sda3        48384000   829790207   390703104    7  HPFS/NTFS/exFAT
/dev/sda4       829790262  1953520064   561864901+   7  HPFS/NTFS/exFAT
Partition 4 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0003147b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  4294967295  2147482624    7  HPFS/NTFS/exFAT

Disk /dev/sde: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf562aa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          32    15633407     7816688    b  W95 FAT32


```

this for gisk -l for sda (Windows Drive):
```
xubuntu@xubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 66877658-9744-4043-9304-5E577CB0EE19
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 7138 sectors (3.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  Microsoft basic data
   2          206848        48383999   23.0 GiB    0700  Microsoft basic data
   3        48384000       829790207   372.6 GiB   0700  Microsoft basic data
   4       829790262      1953520064   535.8 GiB   0700  Microsoft basic data
```

and this for gdisk-l for sdb (Ubuntu Drive):
```
xubuntu@xubuntu:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4EF2CA62-2B3E-472C-BED4-DF18AFA2D74C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3626758253 sectors (1.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          976895   476.0 MiB   8300  
   2          976896        30273535   14.0 GiB    8300  
   3        30273536       264648703   111.8 GiB   8300  
   4       264648704       280272895   7.5 GiB     8200 

```

heres what I have for parted -l:
```
xubuntu@xubuntu:~$ sudo parted -l
Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   24.8GB  24.7GB  primary  ntfs         hidden
 3      24.8GB  425GB   400GB   primary  ntfs
 4      425GB   1000GB  575GB   primary  ntfs


Model: ATA TOSHIBA DT01ACA2 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  500MB   499MB   ext4
 2      500MB   15.5GB  15.0GB  ext4
 3      15.5GB  136GB   120GB   ext4
 4      136GB   143GB   8000MB  linux-swap(v1)


Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2199GB  2199GB  primary  ntfs


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sde: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot


```

and lastly here is the output of blkid:
```
xubuntu@xubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="F8B2812EB280F304" TYPE="ntfs" 
/dev/sda2: LABEL="Recovery" UUID="3EFC8263FC821575" TYPE="ntfs" 
/dev/sda3: LABEL="WIN7" UUID="007A400C7A3FFCC2" TYPE="ntfs" 
/dev/sda4: LABEL="DATA" UUID="1E1401CEFDE8C65B" TYPE="ntfs" 
/dev/sdb1: UUID="442a329a-5762-42bf-ba33-4d614bb148b1" TYPE="ext4" 
/dev/sdb2: UUID="8d3ad1b1-0e42-4783-99e0-50e7b5441d7d" TYPE="ext4" 
/dev/sdb3: UUID="31573cb9-24ec-4543-8272-5e5ed0fca1ee" TYPE="ext4" 
/dev/sdb4: UUID="13ff074f-a74e-46ec-a50a-29096e3f6f63" TYPE="swap" 
/dev/sdc1: UUID="821C029BE662DB27" TYPE="ntfs" 
/dev/sde1: LABEL="UUI" UUID="9A63-63BA" TYPE="vfat" 


```

---

### Post by oldfred on 2014-06-16
Ubuntu will boot from a gpt partitioned drive in BIOS or UEFI if you have the correct supporting partitions bios_grub for BIOS or efi partition for UEFI.
Since Windows is BIOS, much better to have Ubuntu boot in BIOS mode even if hardware supports UEFI.

       If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. 

You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive. It can be anywhere on the drive.

If using gpt with BIOS create a 1 or 2MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

If you ever think drive may be installed in a UEFI system, better to add an efi partition now. It is supposed to be first and does not have to be large or 300MB is usally plenty.

---

### Post by 777funk on 2014-06-16
Thanks to both of you. Is the problem that the 2TB drive (sdb) that I've installed Ubuntu on is GPT partitioned?

With the Automatic Install (Ubuntu partitions as it pleases and uses the whole drive) everything works. But I would prefer to partition as I'd like (i.e. /home directory).

---

### Post by oldfred on 2014-06-16
If just installing Ubuntu to a blank drive and drive is somewhere over 1TB, it will default to gpt. You only have to have gpt if drive is over 2TiB or 2.2TB. But gpt does have some advantages. Main disadvantage if dual booting with Windows is that it will only boot in UEFI mode from gpt drive.
Windows will read gpt partitions if NTFS and booted in BIOS mode. So you can still create a shared NTFS data partition on your gpt drive and see it from Windows.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by 777funk on 2014-06-16
Thanks. Any ideas what course I should take to get this 2TB drive to boot with only Ubuntu on it as an OS? 

I've got a very slow internet connection so each reinstall is pretty painful. I'd like to fix just the boot/grub if I can.

---

### Post by 777funk on 2014-06-16
Just got this result from boot-repair:
[http://paste.ubuntu.com/7655929/](http://paste.ubuntu.com/7655929/)

Also, reinstalling as we speak. The solution to this is a little too much of a mystery. I'll be auto installing this time and will just have to customize the partitions after the fact. 

It will be interesting to see how the auto install partitions things for comparisons sake. I suppose that will tell me what I did wrong manually

---

### Post by 777funk on 2014-06-16
Ok here's what Ubuntu did automatically (creates a working install/boot):

```
Model: ATA TOSHIBA DT01ACA2 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   1992GB  1992GB  ext4
 3      1992GB  2000GB  8256MB  linux-swap(v1)


```

This is the output of parted -l for the drive in question. Comparison to what didn't work is above. Also the ASUS bios shows the drive as UEFI when I enter it upon boot.

---

### Post by oldfred on 2014-06-16
That is an auto install in UEFI mode as you have the FAT32 boot partition.
You will not be able to dual boot from grub as Windows is in BIOS boot mode.
Once you start booting in one mode you cannot switch, or from grub menu you can only boot systems in the same boot mode.
You can also boot from one time boot key, so you do not always have to go into UEFI. But a few systems require you to go into UEFI and turn on or off UEFI mode or BIOS/CSM mode to boot a system in that mode.

You can use Boot-Repair to convert a UEFI install to BIOS boot, but have to use gparted to create the 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive.
Then you could dual boot from grub menu as long as Windows is not hibernated.

Your BootInfo report must be from before the UEFI reinstall as it has no FAT32 efi partition. But it is also missing the bios_grub partition and that is why grub would not install correctly.

Generally with very large drives like your 2TB drive, I do not like the default install. The default worked ok when drives were 100 or even 500GB, but now you have a massive / (root). It is more efficent to have a / of 25GB and use the rest of the drive as /home, data partition(s) or backup partition for Windows files.
I have two data partitions one NTFS (still) even though not booting XP anymore and a Linux formatted data partition for all new data.

---

### Post by 777funk on 2014-06-17
> **oldfred said:**
> That is an auto install in UEFI mode as you have the FAT32 boot partition.
You will not be able to dual boot from grub as Windows is in BIOS boot mode.
Once you start booting in one mode you cannot switch, or from grub menu you can only boot systems in the same boot mode.
You can also boot from one time boot key, so you do not always have to go into UEFI. But a few systems require you to go into UEFI and turn on or off UEFI mode or BIOS/CSM mode to boot a system in that mode.

You can use Boot-Repair to convert a UEFI install to BIOS boot, but have to use gparted to create the 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive.
Then you could dual boot from grub menu as long as Windows is not hibernated.



I'm ok with not having a grub menu at all and just controlling the boot by drive boot sequence in the BIOS when I want Windows. I'd assume all is ok with this??

> 
Your BootInfo report must be from before the UEFI reinstall as it has no FAT32 efi partition. But it is also missing the bios_grub partition and that is why grub would not install correctly.


You're exactly right. That report was while I was still troubleshooting. I'm still not exactly sure if I could replicate a working system manually. This one really has my head spinning... or should I say pulling my hair out. I've never had so much trouble with an installation.

> 
Generally with very large drives like your 2TB drive, I do not like the default install. The default worked ok when drives were 100 or even 500GB, but now you have a massive / (root). It is more efficent to have a / of 25GB and use the rest of the drive as /home, data partition(s) or backup partition for Windows files.
I have two data partitions one NTFS (still) even though not booting XP anymore and a Linux formatted data partition for all new data.

I agree 100%. I would have loved to do a manual install. At this point, I'll probably have to shrink it down to say 120GB or so in GParted.

---

### Post by 777funk on 2014-06-17
I have it working but I'm not sure I could manually duplicate what it was that made things work. Any certain identification of what the problem was?

---

### Post by 777funk on 2014-06-17
Ok! I ended up having to reinstall (ran into a problem after resizing and making a home partition). And... I studied the Ubuntu auto partition setup and duplicated it manually and... It works! I'll add the answer to the problem later. First I want to see if the experienced users here knew the solution. It turned out to be a simple one but of course it had to do with jumping through the right hoops.

---

### Post by oldfred on 2014-06-17
It did not look like your BIOS install had a bios_grub partition which is required on gpt partitioned drive booting in BIOS mode. Ubuntu's installer adds that now where years ago it did not. Grub will not correctly install without the bios_grub partition. 
Or if installing in UEFI mode it creates an efi partition which is required for UEFI booting.

I often suggest having both an efi partition and a bios_grub partition on Linux gpt partitioned drives. But with gpt Windows will only boot in UEFI mode. Often better then to have Windows on a separate drive if possible.

If both systems are in the same boot mode, this will add Windows to grub menu. But if Windows is in a different mode that boot entry will not work and you can only boot from UEFI/BIOS menu.
       sudo update-grub

---

### Post by 777funk on 2014-06-17
Well the solution was related entirely to what OldFred had mentioned. The specifics weren't 100% clear to me but after reverse engineering the Automatic Installer's partitions, everything made sense. Basically with the GPT partition table, the BIOS was reading it as UEFI and without an EFI boot partition... it was a NO GO. 

Here's basically what the Ubuntu CD Auto Installer did but instead of using the entire disk when I Manually installed, I shrunk it to what was needed. The key was EFIboot and FAT32 along with a boot flag as you can see in the attached screenshot.

Thanks very much to all who offered advice.

I now have two completely independent OS's and Drives which is what I was after. I can choose Windows from the BIOS when I want it and don't ever have to wait on a Grub screen. Marking the thread solved.

---

