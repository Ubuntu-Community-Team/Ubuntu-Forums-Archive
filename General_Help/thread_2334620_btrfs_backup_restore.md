---
title: "btrfs backup restore"
date: 2016-08-21
forum: General Help
---

### Post by kusmierz on 2016-08-21
Hi,

I had ubuntu 16.04 on SSD drive (ADATA Premier Pro SP900 M.2 2280), but unfortunately, the SSD died after 4 months after I bought it. I have (or at least I believe I had) full backup, but I can't recover it. I made my backup by creating btrfs snapshot of my whole partition (subvolume @/, probably I missed @/home, which was another subvolume, but I can live without it), then I did something like
```
btrfs send snapshotname mysnapshotname > /file/on/non-btrfs/filesystem
```
 + bzipped it.

Now I'm trying to restore, but... it looks like all my 3 backups are corrupted (?!):

```

truncate -s10G btrfs0 # so I can restore without using real partition/disk
mkfs.btrfs btrfs0
mount btrfs0 /mnt/

btrfs receive -f mybackupfile.btrfs -v --max-errors 0 /mnt/

```

and after some time I have few files in /mnt/mysnapshot/ and an error...

```


At subvol backup
receiving subvol mysnapshot uuid=cbf3b678-af88-6447-b1f5-xxxxx, stransid=7356

ERROR: crc32 mismatch in command.
ERROR: read from stream failed. Bad address
ERROR: read from stream failed. Bad address
Bus error (core dumped)

```

or

```

ERROR: crc32 mismatch in command.
Segmentation fault (core dumped)

```

Why crc32 mismatch? The bzip file was on zfs partition, so there is a little possibility that it corrupted there... md5sums checked. Am I doomed and my backups are ****ups?

---

### Post by T.J. on 2016-08-21
> **kusmierz said:**
> Hi,


Why crc32 mismatch? The bzip file was on zfs partition, so there is a little possibility that it corrupted there... md5sums checked. Am I doomed and my backups are ****ups?

You should make certain that you are using the exact same version of the OS utilities to decompress that was used to create the file. One of them may have a regression that does not play nice with other versions - and causes decompression to fail - even if the file itself is good.  I'd try restoring to a BTFS disk.  It is possible some of the data is unrecognizable to any other formatted drive.
 

A CRC mismatch in most cases means that the data is somewhere between *possibly* and *probably* corrupted, meaning it probably is but I'd think that would throw off your MD5 sums.  You could try copying the data to a different physical medium before attempting decompression.  You might get lucky, and it could be a bad format or disc. 

Your options if that fails are limited.  You can try to do a partial decompression, and save what you can.  Probably the best option to get data back if it is actually corrupt is to send the drive to a recovery expert. 

As an aside, I would never use BTFS or ZFS on a production system.  They are not considered entirely stable or feature complete on Linux.  Using them for critical data is asking for trouble like this.  For backup media, you are better off sticking with EXT4, in my opinion.  You should always test your backups from time to time to make sure they are good.

---

