---
title: "Rescue micro sd card encrypted by Android?"
date: 2016-10-19
forum: General Help
---

### Post by nickdc on 2016-10-19
I made the mistake of choosing "internal storage" after inserting a brand new 32gb Sandisk micro sd into my brand new HTC 10, before I'd read all the caveats available online! After a few weeks use I woke one morning to find a notification from 3.49am that the sd card was missing and should be re-inserted! In ensuing attempts to restore functionality I made a second mistake of doing a factory reset on the phone, which still doesn't recognise it. No critical data lost, but I'm narked at the loss of the sd card; as others have said, once Android 6 has taken over the card it won't be seen in any other device and, I now assume, even the original device once a factory reset is done. After a lot of time trying different things suggested by googling and on the forums I've at last had some luck in getting ubuntu (12.04) to see the card. This happened after I'd taken it out of the card reader and used a samsung usb stick/micro sd card holder. For the first time I got full recognition of the card:

```
nick@nick-build-1:~$ sudo fdisk -lu

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbdcfe60c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   390716864   195358401    7  HPFS/NTFS/exFAT

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f0e0f0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   285794303   142897120+   7  HPFS/NTFS/exFAT
/dev/sda2       285794304   976769023   345487360    f  W95 Ext'd (LBA)
/dev/sda5       491483136   968034303   238275584   83  Linux
/dev/sda6       285796352   491481087   102842368   83  Linux
/dev/sda7       968036352   976769023     4366336   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78b5a2c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1465147391   732573664+   7  HPFS/NTFS/exFAT

[COLOR=#0000ff]WARNING: GPT (GUID Partition Table) detected on '/dev/sdh'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdh: 30.9 GB, 30908350464 bytes
256 heads, 63 sectors/track, 3743 cylinders, total 60367872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1    60367871    30183935+  ee  GPT[/COLOR]
nick@nick-build-1:~$ 
```

Having got that far I thought perhaps now gparted would see it, but gparted just hung, endlessly scanning, with the blue led on the holder flashing continuously. This led flashing happened with card reader too, which made me believe the card was not dead, but being blocked by whatever android has set on to it. I'm out of my depth here, but given the recognition by fdisk, surely there must be a way of reclaiming the card. I'm happy using the terminal but far from familiar with all the commands, so would greatly appreciate someone leading me through an appropriate sequence.

---

### Post by nickdc on 2016-10-20
OK, while waiting to see if someone would come to my aid I've done a bit more reading and risked trying to format the drive using mkdosfs. It hasn't worked, but I got some feedback which I don't fully understand but others no doubt will:

```
nick@nick-build-1:~$ sudo mkdosfs -F 32 -v /dev/sdd
mkdosfs 3.0.12 (29 Oct 2011)
mkdosfs: Device partition expected, not making filesystem on entire device '/dev/sdd' (use -I to override)
nick@nick-build-1:~$ sudo mkdosfs -F 32 -v /dev/sdd1
mkdosfs 3.0.12 (29 Oct 2011)
WARNING: Not enough clusters for a 32 bit FAT!
/dev/sdd1 has 64 heads and 32 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 32768 sectors;
file system has 2 32-bit FATs and 1 sector per cluster.
FAT size is 252 sectors, and provides 32232 clusters.
There are 32 reserved sectors.
Volume ID is ef0c5ac0, no volume label.
mkdosfs: failed whilst writing reserved sector
nick@nick-build-1:~$ 
```

Could someone kindly interpret this for me and tell me what to try next? eg should I have continued trying to write to the whole drive by "using -I to override"? Or was I right to change to sdd1? I'm really in the dark here.

---

### Post by Bucky Ball on 2016-10-20
Is this an sdxc card? A large one? You might need to install exfat-utils and exfat-fuse from the Ubuntu repos using terminal or package manager if so. Not installed by default. Might get you a step in the right direction but not sure about unencrypting it. You'll at least be able to see what's on there in Gparted (and maybe even the folders in a file manager ...).

---

### Post by nickdc on 2016-10-20
Thanks for pitching in, Bucky Ball. To be honest I'm not sure if it's sdx - I find all the different sd card classifications quite confusing these days. It's one of the SanDisk "Extreme" range. On the packaging it says micro SDHC UHS-1. On the card itself there's also a U with a 3 inside it. It's a 32gb card. I'm not bothered about what's on there - it was all backed up or of no consequence. I'd just like to be able to use the card again, not have to bin it.

---

### Post by Bucky Ball on 2016-10-20
You need exfat-utils and exfat-fuse installed, as I said, or you will not be able to use that card in any condition, even brand new.

Install from terminal:

```
sudo apt install exfat-fuse exfat-utils
```

Reboot and try again.

---

### Post by nickdc on 2016-10-21
OK, I've installed the two exfats, (and yes, I did reboot) but still no joy:

```
nick@nick-build-1:~$ sudo umount /dev/sdh
umount: /dev/sdh: not mounted
nick@nick-build-1:~$ sudo mkdosfs /dev/sdh -F32
mkdosfs 3.0.12 (29 Oct 2011)
mkdosfs: Device partition expected, not making filesystem on entire device '/dev/sdh' (use -I to override)
nick@nick-build-1:~$ sudo mkdosfs /dev/sdh1 -F32
mkdosfs 3.0.12 (29 Oct 2011)
WARNING: Not enough clusters for a 32 bit FAT!
mkdosfs: failed whilst writing reserved sector
nick@nick-build-1:~$ sudo mkdosfs /dev/sdh1 -v
mkdosfs 3.0.12 (29 Oct 2011)
/dev/sdh1 has 64 heads and 32 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 32768 sectors;
file system has 2 16-bit FATs and 4 sectors per cluster.
FAT size is 32 sectors, and provides 8167 clusters.
There are 4 reserved sectors.
Root directory contains 512 slots and uses 32 sectors.
Volume ID is 5b7044b8, no volume label.
mkdosfs: failed whilst writing reserved sector
nick@nick-build-1:~$ 
```

I would really appreciate some help interpreting the read-out. 

As I asked before: should I be trying to write the fs to the whole device (/dev/sdh) or the partition (/dev/sdh1)?

---

### Post by nickdc on 2016-10-21
Further information:

I remembered I have an image file of another 32gb sd card which I cloned as a backup, so I thought I'd try using mkusb, which I've found very powerful in the past, to overwrite the problem card with a new image. Mkusb obviously saw the problem card as it was listed with the other potential target drives, but when I clicked to go the the next window where you select the target drive, mkusb crashed - the window vanished and nothing else appeared. I noticed that the led on the card carrier was flashing continuously, as though mkusb were trying to access it but being blocked.

---

### Post by colmax on 2016-10-21
Are you using an adaptor for your card as in full size
Some have a little slide button to write protect
Cheers

---

### Post by nickdc on 2016-10-21
Yes, but it's not a standard adapter; as I said in my o p, it's a usb stick adapter, ie the adapter slots into a usb port on the pc and the micro sd card slots into the end of the adapter. There's no write protect or lock on it. Using the card adapter that came with the micro sd things are even worse - just not seen by the os at all.

---

