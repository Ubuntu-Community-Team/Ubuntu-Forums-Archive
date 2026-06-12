---
title: "Installing Ubuntu in a primary partition replacing Windows"
date: 2015-01-06
forum: General Help
---

### Post by saurabh-ascan on 2015-01-06
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]Initially I was a windows user and had a dual boot system with Ubuntu in one of the logical partitions. Recently, something went wrong with the system and I tried formatting C drive (where windows was installed) and tried reinstalling it. Though the attempt to install windows failed in between, I can login using Ubuntu. Surprisingly, my system works flawlessly now.[/FONT][/COLOR][/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=3]The disk structure using fdisk shows this:[/SIZE]
[/FONT][/COLOR]
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   422823935   211308544    7  HPFS/NTFS/exFAT
/dev/sda3       422823936   423800831      488448   83  Linux
/dev/sda4       423802878   976771071   276484097    f  W95 Ext'd (LBA)
/dev/sda5       504748032   770988031   133120000    7  HPFS/NTFS/exFAT
/dev/sda6       770990080   976771071   102890496    7  HPFS/NTFS/exFAT
/dev/sda7       423802880   496644095    36420608   83  Linux
/dev/sda8       496646144   504745983     4049920   82  Linux swap / Solaris

Partition table entries are not in disk order


[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]I have decided to switch to Ubuntu completely and reinstall it in one of the primary divisions where windows was initially installed (Right now the logical partition hosting Ubuntu has just 40 GB capacity). Further, I want to start afresh 'restructuring' hard disk again (all backups are taken).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can I get a guidance as to how to start with installing Ubuntu again in the primary division (sda 2 may be?) as well as necessary partitions that need to be made (/boot, /home etc)?[/FONT][/COLOR][/SIZE]

---

### Post by mörgæs on 2015-01-06
Hi, welcome to the fora.
If you want to reinstall the easiest way is just to select 'use entire disk for Ubuntu' during the process. You don't have to erase Windows by hand.

---

### Post by mooreted on 2015-01-06
Yeah, I haven't done manual partitioning in a long time. I have two drives. I disconnect my backup drive then just tell Ubuntu to remove everything and install Ubuntu. When it's done, I reconnect the backup drive. I disconnect the backup drive because it originally had Windows 7 on it and sometimes Ubuntu thinks I want to dual boot.

---

