---
title: "External USB HDDs used for RAID1 keep changing /dev identifiers."
date: 2016-03-24
forum: General Help
---

### Post by tcalbrecht on 2016-03-24
Greetings.

I'm trying to use a [Mediasonic Probox HF2-SU3S2]("http://www.mediasonic.ca/product.php?id=1357290977") drive enclosure with Linux software RAID via [FONT=Courier New]mdadm[/FONT]. I have installed 4 drives in the enclosure, with two of the drives (2 TB each) I'm trying to configure as RAID1. The enclosure is connected to my system via USB 3.0.   Initially I can see the two drives as /dev/sdb and /dev/sdd.  When I do the command to create the RAID the enclosure appears to reset (all the panel lights start flashing, and when the enclosure comes back online the drive designations have changed.

Here's a look at what I'm doing:

tom@topcat:~$ lsblk
[FONT=Courier New]NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 698.7G  0 disk
&#9500;&#9472;sda1   8:1    0 694.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part
&#9492;&#9472;sda5   8:5    0   3.8G  0 part [SWAP]
sdb      8:16   0   1.8T  0 disk                [COLOR="#FF0000"] (in the enclosure)[/COLOR]
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part
sdd      8:48   0   1.8T  0 disk                 [COLOR="#FF0000"](in the enclosure)[/COLOR]
&#9492;&#9472;sdd1   8:49   0   1.8T  0 part
sdf      8:80   0   3.7T  0 disk
&#9492;&#9472;sdf2   8:82   0   3.7T  0 part /media/M
sdg      8:96   0 931.5G  0 disk
&#9492;&#9472;sdg1   8:97   0 931.5G  0 part /media/L
sdh      8:112  0 931.5G  0 disk                 [COLOR="#FF0000"](in the enclosure)[/COLOR]
sdj      8:144  0 298.1G  0 disk                 [COLOR="#FF0000"](in the enclosure)[/COLOR]
&#9492;&#9472;sdj1   8:145  0 298.1G  0 part /media/V
sr0     11:0    1  1024M  0 rom

tom@topcat:~$ sudo mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 /dev/sdd1
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=1953411072K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Thu Mar 17 23:04:34 2016
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=1953411072K  mtime=Wed Dec 31 19:00:00 1969
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Thu Mar 17 23:04:34 2016
mdadm: size set to 1953279808K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

tom@topcat:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 698.7G  0 disk
&#9500;&#9472;sda1   8:1    0 694.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part
&#9492;&#9472;sda5   8:5    0   3.8G  0 part [SWAP]
sdc      8:32   0   1.8T  0 disk
&#9492;&#9472;sdc1   8:33   0   1.8T  0 part
sde      8:64   0   1.8T  0 disk
&#9492;&#9472;sde1   8:65   0   1.8T  0 part
sdf      8:80   0   3.7T  0 disk
&#9492;&#9472;sdf2   8:82   0   3.7T  0 part /media/M
sdg      8:96   0 931.5G  0 disk
&#9492;&#9472;sdg1   8:97   0 931.5G  0 part /media/L
sdh      8:112  0 931.5G  0 disk
sdi      8:128  0 298.1G  0 disk
&#9492;&#9472;sdi1   8:129  0 298.1G  0 part
sr0     11:0    1  1024M  0 rom[/FONT]

The drive designations flip between sdb/sdd and sdc/sde.  It's consistent.  In fact, as you can see, all the drives in the enclosure get new designations.

I'm running Ubuntu 14.04 with all the software up-to-date. 

[FONT=Courier New]tom@topcat:~$ uname -a
Linux topcat 3.16.0-36-generic #48~14.04.1-Ubuntu SMP Wed Apr 15 13:11:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

I tried investigating udev to make the drive designators fixed and persistent, but there is nothing unique that I can see between the 2 identical HDDs.  

TIA for any help.

---

### Post by frostschutz on 2016-03-26
You don't make the drive letters consistent. They're served on a first come, first serve basis. Don't rely on them; rely on UUID instead.

If your drive letters change in mid operation, it's possible the USB connection is not stable or you're disconnecting them without first properly freeing the devices. With RAID you not only have to umount but also stop the RAID before disconnecting the disks. If you have even more storage layers (LUKS, LVM, ...) you have to stop those too.

Failing to do so will cause drive letter changes because the disconnected disks are still "in use" (by the filesystem or RAID) and after reconnect the (same) drives will get new letters because the old ones are not free.

For unexpected drive letter changes look at `dmesg`, it should tell a story.

---

### Post by SeijiSensei on 2016-03-27
To get the UUIDs for the partitions, run the command "sudo blkid" from a command prompt.  Then use the UUID syntax to define the drives in mdadm.conf.

Simple things like plugging in a USB drive can cause the drives to be assigned different /dev/sdX names.  UUIDs are fixed.

---

