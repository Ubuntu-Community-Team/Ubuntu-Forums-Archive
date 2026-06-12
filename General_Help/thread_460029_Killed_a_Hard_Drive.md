---
title: "Killed a Hard Drive"
date: 2007-05-31
forum: General Help
---

### Post by regomodo on 2007-05-31
Hi, i'm hoping i can solve this major problem i have.

I just tried to install DSL to a CF card through an IDE converter. That went well and all the files are in it. However, i cannot access the Hard Drive the CF card was attached to (same ide cable).

I couldn't get it to mount in Ubuntu and when trying to manually mount it i get the following error
```

jon@jon-ubuntu:~$ sudo mount /dev/hdc1 /media/hdc5
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


ext2ifs (windows) saw it but as a 450MB used partition

Knoppix found it but i got an error shown below

Also, i've noticed my XP partition has gone funny. Can only use safe mode. Can't see why as it's on a totally different drive (sata)

Please help, i have 60Gigs of music. Plenty of pics (unfortunately i haven't backed up the last 3months) and a fair amount of vids

---

### Post by regomodo on 2007-05-31
Oh crap, i had the adaptor set to master drive. The other hard drive was set to master as well. The DSL install couldn't have written to both, right?

I found this 

[http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/](http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/)

but i don't want to touch the drive until i know what i should do

---

### Post by taurus on 2007-05-31
One has to be a master and the second one has to be a slave drive.  So, set the jumpers on the back of the second to slave and see if the BIOS detects both.  Then, post the output of this command from a terminal here.

```
sudo fdisk -l
```

---

### Post by regomodo on 2007-05-31
Yeah, i know. The CF drive isn't in now. I pulled it out

```
jon@jon-ubuntu:~$ fdisk -l

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         993      500440+  83  Linux
jon@jon-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         993      500440+  83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        5100    20482875   83  Linux
/dev/sda3            5101        5165      522112+  82  Linux swap / Solaris
/dev/sda4            5166       60801   446896170   83  Linux

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         993      500440+  83  Linux
```

HDC1 is the drive i'm after

Oh, bios detected both and i've removed /dev/hdc1 from fstab, just in case.

---

### Post by regomodo on 2007-05-31
bump

---

### Post by regomodo on 2007-05-31
hmm. was hoping someone would help by the time i got back from the pub.

 I guess i'll have to figure out my issues by myself, again

---

### Post by regomodo on 2007-05-31
```
jon@jon-ubuntu:~$ sudo dumpe2fs /dev/hdc | grep -i superblock
dumpe2fs 1.40-WIP (14-Nov-2006)
dumpe2fs: Bad magic number in super-block while trying to open /dev/hdc
Couldn't find valid filesystem superblock.

jon@jon-ubuntu:~$ sudo e2fsck -b 32768 /dev/hdc1
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Invalid argument while trying to open /dev/hdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

jon@jon-ubuntu:~$ sudo e2fsck -b 8193 /dev/hdc1
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Invalid argument while trying to open /dev/hdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

jon@jon-ubuntu:~$ sudo fsck /dev/hdc -t ext3
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/hdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


jon@jon-ubuntu:~$ sudo gpart -v /dev/hdc

dev(/dev/hdc) mss(512) chs(24321/255/63)(LBA) #s(390716865) size(190779mb)
Primary partition(1)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 488mb #s(1000881) s(63-1000943)
   chs:  (0/1/1)-(992/15/63)d (0/1/1)-(62/77/63)r
   hex:  00 01 01 00 83 0F FF E0 3F 00 00 00 B1 45 0F 00

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


Begin scan...
Possible extended partition at offset(7mb)
   Possible partition(Linux ext2), size(190771mb), offset(7mb)
      type: 131(0x83)(Linux ext2 filesystem)
      size: 190771mb #s(390700736) s(16128-390716863)
      chs:  (1/1/1)-(1023/254/63)d (1/1/1)-(24320/254/62)r
      hex:  00 01 01 01 83 FE FF FF 00 3F 00 00 C0 9E 49 17

End scan.

Checking partitions...
Partition(Linux ext2 filesystem): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 131(0x83)(Linux ext2 filesystem)
   size: 190771mb #s(390700736) s(16128-390716863)
   chs:  (1/1/1)-(1023/254/63)d (1/1/1)-(24320/254/62)r
   hex:  00 01 01 01 83 FE FF FF 00 3F 00 00 C0 9E 49 17

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```

Holy crap. It isn't looking good

---

### Post by taurus on 2007-05-31
See if you can format it to ext3 with gparted (System -> Administration).  Otherwise, you can try it from a terminal like

```
sudo mke2fs -j /dev/hdc1
sudo mkdir /media/hdc1
sudo mount -t ext3 /dev/hdc1 /media/hdc1
df -h
```

---

### Post by regomodo on 2007-05-31
won't that wipe everything?

---

### Post by taurus on 2007-05-31
> **regomodo said:**
> won't that wipe everything?

Yip.  It will reformat /dev/hdc1 so everything will be gone.

---

### Post by regomodo on 2007-05-31
> **taurus said:**
> Yip.  It will reformat /dev/hdc1 so everything will be gone.
that kinda defeats the outcome i was after. I'm going to try Stellar Phoenix Linux first

---

### Post by regomodo on 2007-05-31
Damn, i'm pretty sure it's shafted. Just tried that app, couldn't find a partition after a long search.

Backup, backup, backup. Just wanted those 3 months of pics from my D70, nothing else. You would have thought i'd have learned after losing a load almost year ago.

Fsck

---

### Post by regomodo on 2007-06-01
Yep, definetly dead. Ran that special app which  "downloaded". It found absolutely nothing. It moaned about the state the drive was in. That took about 7hrs to scan the 200GB drive intensively. Reformatted it and it works fine. Thankfully i was able to get some data back, although that was my RAW files from a holiday using "PC Inspector Smart Recovery" on a CF card.

I'm now looking at making a raid5 fileserver for all my data for the future. I'm not going to make the same mistake for a 3rd time!

---

