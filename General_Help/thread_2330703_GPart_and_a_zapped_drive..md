---
title: "GPart and a zapped drive."
date: 2016-07-13
forum: General Help
---

### Post by Evil Wayz on 2016-07-13
I was fumbling in the dark for the power cable to my backup drive, and I accidentally plugged my laptop adapter into my  WD My Book.  That resulted in a loud bang and a puff of smoke.

So I tore the drive out of the enclosure, and added it as a third drive.  It shows up as the correct hard drive in bios, and it also shows up in gparted.  But it shows up as 2 TB of unallocated space.  Now, I have accidentally deleted a partition table before, and it was my understanding that if you don't create a new one over it, you can usually retrieve it.

Using this old tutorial [http://ubuntuforums.org/showthread.php?t=370121]("http://ubuntuforums.org/showthread.php?t=370121")

I started the process, and the following error pops up on almost every sector:

Warning: read error (EIO) near sector 578554127), skipping

Obviously the sector changes each time.

Is there another recovery method I could use or is this drive completely humped?  


I am running 16.04 lts, 4.4 kernel.  The drive was an NTFS drive.

---

### Post by QDR06VV9 on 2016-07-13
I have had very good results with Testdisk. But I have never had a power surge as you described.
[https://www.maketecheasier.com/recover-data-and-partitions-for-free-with-testdisk/](https://www.maketecheasier.com/recover-data-and-partitions-for-free-with-testdisk/)
And I wish you the best of luck

---

### Post by Evil Wayz on 2016-07-15
First scan couldn't recover the partition.  Trying deeper scanning.  Things are looking mighty bleak.

---

### Post by Evil Wayz on 2016-07-15
So its showing an NTFS partition, and the only error is:

```
 Read Error at 2119/06/60 (lba=34045952)
```

But at the end of both scans, partition was unrecoverable.  I hesitate to use the advanced settings without some guidance.

---

### Post by QDR06VV9 on 2016-07-15
> **Evil Wayz said:**
> So its showing an NTFS partition, and the only error is:

```
 Read Error at 2119/06/60 (lba=34045952)
```

But at the end of both scans, partition was unrecoverable.  I hesitate to use the advanced settings without some guidance.

Crap Evil Wayz if I was setting at your computer I could help but I am not so I do not feel good about any advice on what to do next?
But the good news is I think your are at the very least going to able to recover needed data,,IE Pics, Documents etc etc.
Sit tight and wait for someone to come along with better skills on this.
Or head over to their forums: [https://forum.cgsecurity.org/phpBB3/](https://forum.cgsecurity.org/phpBB3/)

---

### Post by Evil Wayz on 2016-07-15
Thanks for the link... I think the fact that i removed the drive from a wd external is part of the problem, apparently there is some sort of encryption involved with the sata adapter.

---

