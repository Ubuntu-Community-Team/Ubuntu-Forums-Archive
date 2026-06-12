---
title: "Having an issue booting to Ubuntu 20.04"
date: 2022-03-21
forum: General Help
---

### Post by mystery-incognito on 2022-03-21
I have Ubuntu 20.04 on a dedicated boot drive. I do use a physical switch that switches between hard drives for Ubuntu and my Windows drive. Windows boot drive works just fine. 

When I try to use Ubuntu, it says "Reboot and Select proper Boot device or Insert Boot Media and press a key"

It has been working for over a year. I saw online that boot repair could work so I used the installation USB, closed the installation which allows me to "try Ubuntu" from the USB drive. 

Boot repair says:

```

============================== Boot Info Summary ===============================
 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.
sdb1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 16400 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi /ldlinux.sys
================================ 0 OS detected =================================
================================ Host/Hardware =================================
CPU architecture: 64-bit
Video: GK106 [GeForce GTX 650 Ti] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04 LTS, focal, x86_64)
===================================== UEFI =====================================
BIOS/UEFI firmware: V1.8 from American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).
============================= Drive/Partition Info =============================
Disks info: ____________________________________________________________________
Partitions info (1/3): _________________________________________________________
Partitions info (2/3): _________________________________________________________
Partitions info (3/3): _________________________________________________________
fdisk -l (filtered): ___________________________________________________________
Disk sda: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk sdb: 3.75 GiB, 4009745920 bytes, 7831535 sectors
Disk identifier: 0x3ef2048a
      Boot Start     End Sectors  Size Id Type
sdb1  *     2048 7831534 7829487  3.8G  c W95 FAT32 (LBA)
parted -lm (filtered): _________________________________________________________
sda:120GB:scsi:512:512:unknown:ATA SATAFIRM S11:;
sdb:4010MB:scsi:512:512:msdos:SCSIDISK SCSI_DISK_1234:;
1:1049kB:4010MB:4009MB:fat32::boot, lba;
blkid (filtered): ______________________________________________________________
NAME   FSTYPE   UUID                                 PARTUUID                   
LABEL       PARTLABEL
sda                                                                             
sdb                                                                             
âJJâJJsdb1 vfat     7A6C-37C5                            3ef2048a-01            
UBUNTU 20_0 
Mount points (filtered): _______________________________________________________
           Avail Use% Mounted on
/dev/sdb1    1.2G  68% /cdrom
Mount options (filtered): ______________________________________________________
/dev/sdb1   vfat            
ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-
1,shortname=mixed,errors=remount-ro
====================== sdb1/boot/grub/grub.cfg (filtered) ======================
Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
========================= sdb1/syslinux.cfg (filtered) =========================
DEFAULT loadconfig
LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
==================== sdb1: Location of files loaded by Grub ====================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
================== sdb1: Location of files loaded by Syslinux ==================
           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
Suggested repair: ______________________________________________________________
The default repair of the Boot-Repair utility would not act on the boot.

```

Any idea how I can recover my Ubuntu drive?

---

### Post by tea for one on 2022-03-21
The boot repair report is incomplete e.g. your Windows drive is not listed
[COLOR="#0000FF"]0 OS detected[/COLOR] - No sign of any operating system
[COLOR="#0000FF"]sda:120GB:scsi:512:512:unknown:ATA SATAFIRM S11:;[/COLOR] - Is this the expected location of Ubuntu?

Is your physical switch functioning OK?

Can you run the boot-repair report again with all the drives attached and accessible?

---

### Post by mystery-incognito on 2022-03-21
The windows drive is powered via a physical switch so it wouldn't be listed. If you press it one way, it will only supply power to the windows drive, the other, it will supply power to the Linux drive. The windows drive shouldn't be listed. If I run both, there will be a problem as they both believe they are the only drive. I believe Linux is on the drive 
sda:120GB:scsi:512:512:unknown:ATA SATAFIRM S11:;

---

### Post by dragonfly41 on 2022-03-21
I have no experience of power switched dual boot.

I read this:
BIOS/UEFI firmware: V1.8 from American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).   

It it was UEFI mode (instead of legacy) I might suggest to try installing rEFInd as boot.

---

### Post by oldfred on 2022-03-21
Newer UEFI systems, forget a boot entry whenever a drive is disconnected.
So you have to recreate new UEFI boot entry everytime you switch.

You may be able to boot a fallback or drive entry not the "ubuntu" entry as that drive entry is how external drives all boot. 
Ubuntu normally adds the fallback entry at /EFI/Boot/bootx64.efi in ESP.

---

### Post by mystery-incognito on 2022-03-22
The motherboard is about 10 years old, using BIOS not UEFI as far as I can tell. I've been switching between the two drives without any problems for almost two years since 20.04 came out.

If somehow it did manage to forget a boot entry, how would I rectify that? The only thing I notice that could be an issue is if I am on one drive too long before switch to the other, the time is usually off. It's just completely off (not the previous time, current time nor the motherboard time, just some random time altogether but within about half a day of current time.)

I was entering the boot repair by running it from the USB drive.

I read online that fsck sometimes works as a fix. Any opinions?

---

### Post by tea for one on 2022-03-22
Two suggestions:-

Fsck only works with partitions but they have not been identified yet.
With the switch set to the Ubuntu drive, can you boot into a live session and run via the terminal:-
```
sudo parted -l
```
Please post the output using Adv Reply > **#** (i.e. Wrap [CODE] tags round selected text)

Assuming your switch allows you to boot Windows, are you able to swap the drives to see if your Ubuntu drive boots?

---

### Post by mystery-incognito on 2022-03-23
I'm able to boot to windows, however even with the other drive directly plugged in (no switch) there is no difference. 

When I tried:

```
sudo parted -l
```

I got: 

```
Error: /dev/sda: unrecognised disk label
Warning: Error fsyncing/closing /dev/sda: Input/output error
Retry/Ignore? i                                                           
Model: ATA SATAFIRM S11 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: SCSIDISK SCSI_DISK_1234 (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4010MB  4009MB  primary  fat32        boot, lba
```

When I tried to use fsck I got: 

```
umount /dev/sdb

umount: /dev/sdb: not mounted.

fsck /dev/sdb

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sdb is in use.
e2fsck: Cannot continue, aborting.


```

---

### Post by tea for one on 2022-03-23
```
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4010MB  4009MB  primary  fat32        boot, lba
[COLOR="#0000FF"]This disk (sdb) 4010MB is your USB stick used in your live session, hence in use[/COLOR]
```
```
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
[COLOR="#0000FF"]This disk (sda) does not have a partition table, therefore lacking a file system, operating system and data.[/COLOR]
```

If sda was the original location of Ubuntu, regrettably it is no longer there.

Do you know what happened?

You will have to re-install Ubuntu and restore your backups.

In the boot-repair report, there was mention of [COLOR="#0000FF"]BIOS/UEFI firmware: V1.8 from American Megatrends Inc[/COLOR], it would be advantageous if you could establish if your PC is UEFI capapble.
If possible, both Windows and Ubuntu should be installed in UEFI mode with GPT.

---

### Post by mystery-incognito on 2022-03-24
No it's not possible for it to use UEFI. Thanks for your advice. I'll keep trying I think there must be a way, my guess is maybe there was an update I was unaware of and maybe switched clearing the temporary items that get stored on reboot.

---

