---
title: "MDADM: Add existing RAID0 array (2x2TB) to a new RAID1 (RAID0-array + 1x4TB)"
date: 2014-02-16
forum: General Help
---

### Post by Daniel_Jnger on 2014-02-16
Hello everyone!

I've created a RAID0 array using mdadm and 2x2TB drives [COLOR=#ff0000](only for data. root-system and swap are on another drive)[/COLOR]. 

```
root@server:~# cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdd1[1] sdc1[0]
      3907025920 blocks super 1.2 512k chunks


unused devices: <none>




```

I've also got a single 4TB drive wich I would like to use as a mirror for the RAID0 array.


Is there any possibility doing that (maybe without loosing the data on the existing RAID0)?

Since I used mdadm before, I know about it's functionality, but I'm a bit scared loosing all the data. Therefore I'd like to ask for some help from someone who has got a little more experience than me.

Sorry for the german language setting ;) :
```
root@server:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 KÃ¶pfe, 63 Sektoren/Spur, 121601 Zylinder, zusammen 1953525168 Sektoren
Einheiten = Sektoren von 1 Ã 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Festplattenidentifikation: 0x00045e2d


   GerÃ¤t  boot.     Anfang        Ende     BlÃ¶cke   Id  System
/dev/sda1            2048  1953523711   976760832   83  Linux


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 KÃ¶pfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 Ã 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x0005331f


   GerÃ¤t  boot.     Anfang        Ende     BlÃ¶cke   Id  System
/dev/sdb1       480583678   488396799     3906561    5  Erweiterte
/dev/sdb2   *        2048   480581631   240289792   83  Linux
/dev/sdb5       480583680   488396799     3906560   82  Linux Swap / Solaris


PartitionstabelleneintrÃ¤ge sind nicht in Platten-Reihenfolge


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 KÃ¶pfe, 63 Sektoren/Spur, 243201 Zylinder, zusammen 3907029168 Sektoren
Einheiten = Sektoren von 1 Ã 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Festplattenidentifikation: 0x0009bb56


   GerÃ¤t  boot.     Anfang        Ende     BlÃ¶cke   Id  System
/dev/sdc1            2048  3907028991  1953513472   fd  Linux raid autodetect


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 KÃ¶pfe, 63 Sektoren/Spur, 243201 Zylinder, zusammen 3907029168 Sektoren
Einheiten = Sektoren von 1 Ã 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Festplattenidentifikation: 0x000b5450


   GerÃ¤t  boot.     Anfang        Ende     BlÃ¶cke   Id  System
/dev/sdd1            2048  3907028991  1953513472   fd  Linux raid autodetect


Disk /dev/sde: 4000.8 GB, 4000787030016 bytes
255 KÃ¶pfe, 63 Sektoren/Spur, 486401 Zylinder, zusammen 7814037168 Sektoren
Einheiten = Sektoren von 1 Ã 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Festplattenidentifikation: 0x00000000


Festplatte /dev/sde enthÃ¤lt keine gÃ¼ltige Partitionstabelle


Disk /dev/md0: 4000.8 GB, 4000794542080 bytes
2 KÃ¶pfe, 4 Sektoren/Spur, 976756480 Zylinder, zusammen 7814051840 Sektoren
Einheiten = Sektoren von 1 Ã 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Festplattenidentifikation: 0x00000000


Festplatte /dev/md0 enthÃ¤lt keine gÃ¼ltige Partitionstabelle



```
short:
sda --> drive for backup
sdb --> system drive
sdc,sdd --> 2TB
sde --> 4TB
md0 --> (sdc + sdd) as RADI0 array

[COLOR=#ff0000]**What I need is: (md0 + sde) as a RAID1 array**[/COLOR]


Thanks in advice!

---

### Post by metalfan49 on 2014-08-26
Kind of an old thread, but no replies and I'm in a similar situation with mismatched drives, so here's what I found.  Mdadm happily enough lets you make a new RAID1 devices from the 2 smaller drives in RAID0, and the larger drive.  I tested this in a VM and it appeared to be working okay, with all three virtual disks churning when I moved data around on the RAID1 device.  I didn't do any extensive testing or benchmarking, but, it appears that it's working just how you'd think it would.

To set it up with your existing volume with data, I think you have to create a degraded RAID1 from the single 4TB drive, then copy all your data to it.  Then you can add the RAID0 device to the degraded RAID1 array, and let MDADM sync the data from the single drive member of the RAID1, over to the original md0 (sdc + sdd).  It's kind of unfortunate that it basically will be copying the data completely twice before it's usable, but it's the only documented way I found, although I didn't search too long.  I found it described here: [https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID) .  Since in your case (and mine), we just had data volumes and not the whole system, it's a much simpler process than all that on the wiki, since we can skip the stuff relating to making it bootable.

---

