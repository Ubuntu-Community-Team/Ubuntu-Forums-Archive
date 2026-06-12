---
title: "veracrypt + rsync = low transfer speed plus CPU core saturation"
date: 2018-09-22
forum: General Help
---

### Post by mikeymikec on 2018-09-22
Lubuntu 18.04 LTS 64-bit
Core i5-4690K, stock speed
12GB RAM
Source disk:  WD Black 1TB SATA3 connected internally
Destination disk:  WD Black 500GB connected via USB3
Both file systems are NTFS (I migrated from Windows a few months ago).

If I transfer using the standard file manager, I get file transfer speeds (monitoring using iotop) in the realm of 100MB/sec (give or take say 30MB/sec).  If I transfer with rsync, I get a transfer speed of about 35MB/sec and one CPU core being constantly saturated.

cp gives similar throughput to the standard file manager's transfer mechanism.

A friend suggested I do rsync without checksum checking (I found the switch 'size-only') but that made zero difference.

I'm doing this for backup purposes.  On Windows I'd normally use robocopy in order to sync two file system structures from the command line, AFAIK rsync is the nearest equivalent.

---

### Post by TheFu on 2018-09-22
NTFS is known to have poor transfer performance.  There is 1 mount option which can help, big_writes.

**rsync** has different behaviors when all the storage is directly connected compared to over-the-network transfers. The manpage has different ways to get around it.

---

### Post by mikeymikec on 2018-09-22
Are you suggesting that rsync performs poorly with NTFS?  Otherwise I'm not sure if you factored in the far better performance I experienced when transferring with cp/pcmanfm to the same volume.

---

### Post by TheFu on 2018-09-22
> **TheFu said:**
> NTFS is known to have poor transfer performance.  There is 1 mount option which can help, big_writes.

is what I said.  The poor performance is NTFS specific.  If you don't use NTFS and use Linux file systems, then that issue will go away.
If you tack on veracrypt and choose a cipher that doesn't have CPU hardware support, then it will be a little worse.

rsync on local to local sync behaves differently than it does between local and remote sync.  No mention of NTFS or EXT3 or other Linux file systems. The manpage does mention something about FAT being slower.

The magic of rsync really works best over remote syncs and when most of the files already exist on both systems.  The first copy will be a full copy. Nothing can change that.

---

### Post by TheFu on 2018-09-22
> **TheFu said:**
> NTFS is known to have poor transfer performance.  There is 1 mount option which can help, big_writes.

is what I said.  The poor performance is NTFS specific.  
If you tack on veracrypt and choose a cipher that doesn't have CPU hardware support, then it will be a little worse.

rsync on local to local sync behaves differently than it does between local and remote sync.  No mention of NTFS or EXT3 or other Linux file systems. The manpage does mention something about FAT being slower.

The magic of rsync really works best over remote syncs and when most of the files already exist on both systems.  The first copy will be a full copy. Nothing can change that.

---

### Post by mikeymikec on 2018-09-23
I just formatted the volume as ext3 and I get exactly the same symptoms (ie. rsync slow throughput and CPU core saturation, not with cp or copying through pcmanfm).

---

### Post by mikeymikec on 2018-09-23
mea culpa, I figured it out.  I think what happened originally was that while writing my first script, I was reading the man page for rsync, saw the 'z' (compress) option and thought it looked interesting with a "try it, it might work out quite well, or remove it when it probably doesn't" idea in mind, saved the script, came back to it weeks later and forgot about me wanting to try that option out, then wondered why the backup was taking so long :)

I found this guide:
[https://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/](https://www.howtogeek.com/135533/how-to-use-rsync-to-backup-your-data-on-linux/)
```
rsync -av --delete /Directory1/ /Directory2/
```

Stripped down the switches I was using to just what they recommended, lo and behold a bit of decent throughput!

---

### Post by TheFu on 2018-09-23
Glad you figured something out! We've all been there. ;)  Without seeing the exact command used, nobody here would have guessed. 
For networked rsync transfers, using compression can help greatly.  It gets in the way on CPU-bound systems.

If you are still using NTFS, use the mount option above to see some huge additional throughput, 30% more is common from what I've read.

---

