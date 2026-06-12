---
title: "External USB drive not recognised, bad superblock"
date: 2018-08-05
forum: General Help
---

### Post by taxiclette on 2018-08-05
Hi,

I have a solid state drive, coming from a broken MacBook. a 160 GB SSD USB2 Drive in a Icy Box holder. It is formatted FAT, so I could use it on my Raspberry Pi (3, model B) (Raspbian Stretch), on my HP with Ubuntu (18), on my work (Xubuntu) and on my Mac. I used it for months without a problem.
One day, I think I removed the disk wrong and it appeared as "MUZIK1" (the original name being "MUZIK"). Both MUZIK and MUZIK1 appeared on the desktop, but MUZIK was empty. That was on my Raspberry. The disk kept working for the coming times. I finally had the money for a new MacBook and there, the disk wasn't accepted. I could use disk utility, I only could format the drive. I didn't do that, of course.
Now yesterday I put a lot of files in my MegaCloud folder on the Raspberry, which worked, but took a long time (hours). At work, I still could use the drive as well, in Xubuntu. The first time I had trouble reading the drive, was on Ununtu (HP desktop). What happens:
[LIST]
[*]I hear the click-noise indicating a drive is detected, but I can't see the drive anywhere (not on the desktop, not in media/username/...) 
[*]Gparted doesn't see the drive, Disks does see it, but I can only change the mounting options. I tried that, but that didn't make a difference. It shows up in media/username/... if I say to call it sdb, but it's not possible to open), testdisk doesn't see the drive. 
[*]I tried on the Xubuntu desktop at work and my Raspberry, but nothing to see there either. The Xubuntu also gives the noise indication it detects something. 
[/LIST]

I searched some forums and tried some stuff. Nothing worked so far, but at a given point, I had the message that there was a bad superblock. I can't reproduce what I did. The tricks to repair the bad superblock-problem, where for ext2/3, not for FAT. Somewhere I also saw that my drive would be msdos, not FAT and I read that that would mean it is a MBR. I'm not sure if that was really about the SSD, because, as you see underneath, sometimes I got info of my harddrive sda instead of the external drive sdb.

The name of the drive appears to be CT250BX1 00SSD1

sudo fdisk -l gives this output:
[INDENT]Schijf /dev/loop0: 517,2 MiB, 542310400 bytes, 1059200 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes

Schijf /dev/loop1: 86,9 MiB, 91099136 bytes, 177928 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes

Schijf /dev/loop2: 515,1 MiB, 540069888 bytes, 1054824 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes

Schijf /dev/loop3: 6,3 MiB, 6610944 bytes, 12912 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes

Schijf /dev/loop4: 86,6 MiB, 90812416 bytes, 177368 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes

Schijf /dev/loop5: 86,9 MiB, 91115520 bytes, 177960 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes

Schijf /dev/loop6: 517,2 MiB, 542277632 bytes, 1059136 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes

Schijf /dev/sda: 149,1 GiB, 160041885696 bytes, 312581808 sectoren
Eenheid: sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logisch/fysiek): 512 bytes / 512 bytes
In-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijflabeltype: dos
Schijf-ID: 0xc74496a8

Apparaat   Op.   Begin     Einde  Sectoren Grootte ID Type
/dev/sda1         2048   4208639   4206592      2G 82 Linux wisselgeheugen
/dev/sda2  *   4208640 312580095 308371456    147G 83 Linux
[/INDENT]

sudo fsck.msdos /dev/sdb or sudo fsck.vfat /dev/sdb give this output:
[INDENT]fsck.fat 4.1 (2017-01-24)
Got 0 bytes instead of 512 at 0[/INDENT]

sudo parted -l /dev/sdb gives this output, but that isn't the information of sdb, it's that of the harddrive in my computer itself:[INDENT]Model: ATA ST3160318AS (scsi)
Schijf /dev/sda: 160GB
Sectorgrootte (logisch/fysiek): 512B/512B
Partitietabel: msdos
Schijfvlaggen: 

Nummer  Begin   Einde   Grootte  Type     Bestandssysteem  Vlaggen
 1      1049kB  2155MB  2154MB   primary  linux-swap(v1)
 2      2155MB  160GB   158GB    primary  ext4             opstart
[/INDENT]


lsusb gives this:
[INDENT]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 4168:1004 Targus 
Bus 001 Device 004: ID 357d:7788 Sharkoon QuickPort XT
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:07f8 Microsoft Corp. Wired Keyboard 600 (model 1576)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/INDENT]
(Targus is my mouse, I have a Dell schreen with powered hub) I tried all USB ports: front in computer, powered hubs in screen.

mount /dev/sdb:[INDENT]mount: /dev/sdb: can't find in /etc/fstab.[/INDENT]

dmesg:

[INDENT][    3.098953] sd 6:0:0:0: [sdb] Unit Not Ready
[    3.098956] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[    3.098961] sd 6:0:0:0: [sdb] ASC=0x44 <<vendor>>ASCQ=0x81 
[    3.099329] sd 6:0:0:0: [sdb] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.099332] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[    3.099336] sd 6:0:0:0: [sdb] ASC=0x44 <<vendor>>ASCQ=0x81 
[    3.099704] sd 6:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.099706] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[    3.099710] sd 6:0:0:0: [sdb] ASC=0x44 <<vendor>>ASCQ=0x81 
[    3.100455] sd 6:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[    3.100457] sd 6:0:0:0: [sdb] 0-byte physical blocks
[    3.100828] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    3.100953] sd 6:0:0:0: [sdb] Asking for cache data failed
[    3.100958] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.101835] sd 6:0:0:0: [sdb] Unit Not Ready
[    3.101837] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[    3.101840] sd 6:0:0:0: [sdb] ASC=0x44 <<vendor>>ASCQ=0x81 
[    3.102204] sd 6:0:0:0: [sdb] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.102207] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[    3.102211] sd 6:0:0:0: [sdb] ASC=0x44 <<vendor>>ASCQ=0x81 
[    3.102579] sd 6:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.102582] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current] 
[    3.102586] sd 6:0:0:0: [sdb] ASC=0x44 <<vendor>>ASCQ=0x81 
[    3.104080] sd 6:0:0:0: [sdb] Attached SCSI disk[/INDENT]


How can I fix this problem?

Kind regards,

Jonathan

---

### Post by dragonfly41 on 2018-08-05
Here is one thread I found explaining how to FAT repair using testdisk.

[https://ubuntuforums.org/showthread.php?t=2103994](https://ubuntuforums.org/showthread.php?t=2103994)

full testdisk workflow explained here ..

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

although I see that you have written ...

> [COLOR=#000000]testdisk doesn't see the drive.[/COLOR]

---

### Post by oldrocker99 on 2018-08-05
I had this problem with a 1TB portable drive, which I could not fix, with similar error messages. It was a Xmas gift, so it really wasn't that much of a loss.

Still, I would really like to find out how to repair a bad superblock. It was, I think, formatted as ext4, which I do with every hard drive I get. Of course.

---

### Post by dragonfly41 on 2018-08-05
There are other threads around for ext4 ...
[https://ubuntuforums.org/showthread.php?t=1245536](https://ubuntuforums.org/showthread.php?t=1245536)

---

