---
title: "Causes of file system corruption?"
date: 2008-04-18
forum: General Help
---

### Post by svivian on 2008-04-18
I've just managed to get my system back in working order after a scary couple of hours of disk corruption, fsck-ing (don't read that word to fast!) and a read-only root file system...

Just wondering, are there any common causes of filesystem corruption? I don't want this to be happening too often :(

 I thought it could be a full disk but I'm only using about 7GB out of at least 20GB (or 30GB, I forget) I partitioned.

Around the time it happend, I had downloaded a couple of torrents. I had also been running a Java program that was writing some stuff to a local database. Neither of these were writing much though...

Any other possible causes?

---

### Post by kd5ful on 2008-04-18
yeah, me too.
...and how do I keep it from happening again, like running a defrag or something???

---

### Post by articpenguin on 2008-04-18
use a journalling filesystem they reduce the chance of corrupton. there are 4 journalling filesystems in the main kernel. They are ext3,jfs,reiserfs,xfs. 

if you want more data saftey over speed use ext3.
If you want a trade off with more speed and less data reliableity use jfs.

Dont use reiserfs or xfs as they corrupt way to easy.


PS: if you want the most data safety use ext3 with journal data mode. This journals everything data and metadata. This will make it very slow.

---

### Post by cdenley on 2008-04-18
Filesystem corruption is usually caused by hardware failure or power failure.

hardware failure
-bad hard drive
-bad memory
-overheated cpu

power failure
-power loss
-turning off while a filesystem is mounted

If you always shutdown your computer properly, and have working hardware, your filesystem should never be corrupt. If you have shutdown your computer properly and still experience filesystem corruption, the first thing I would do is run memtest86 from the grub boot menu.

---

### Post by malangaman on 2008-04-18
The coating on the Hard Disk Drive surface begins to flake and pit with time. Forming a type of electronic memory dementia, or computer Alzheimer's in the last months of an HDD. 

You begin to get "bad sectors". The OS has tools you can run to keep track of these and not write new data on them. Eventually, a critical part of the HDD will fail, such as the Master Boot Record, for example and then you might as well use it for a paper weight.

Your refrigerator compressor can turn on and cause electric variations that can affect the HDD suddely while it is writing, for example. The electric current from the power company may have voltage spikes and drops. That is why a good UPS to keep the current stable between your computer and the electric outlet is essential to prevent file corruption and hardware problems that are even worse.

---

### Post by bingoUV on 2008-04-18
Which filesystem was it? A good filesystem should never get corrupted except for sudden especially unlucky occurrence of bad blocks  / physical injury to the hard disk.

---

### Post by oldos2er on 2008-04-18
"Any other possible causes?"

 What filesystem are you using?

---

### Post by svivian on 2008-04-18
It's ext3, so from what arcticpenguin said it should be stable. The line from my fstab is:
```
UUID=72eaa894-68ee-4268-aa8a-17d60a23a14f / ext3 defaults,errors=remount-ro 0 1
```
(I'm assuming the *errors=remount-ro* part is the bit that made my whole filesystem read-only)

When I ran fsck the first time there were dozens of errors (I pressed 'y' a lot!). There were a few errors the second time (after I figured out that I needed to boot in 'safe mode' and run fsck/remount).

Someone mentioned interference - what about interference from a cordless phone? It wasn't near my computer when the system started breaking last night but I do sometimes leave the handset on top of my pc box...

---

