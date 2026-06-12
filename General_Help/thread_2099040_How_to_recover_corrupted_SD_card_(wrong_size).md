---
title: "How to recover corrupted SD card (wrong size)?"
date: 2012-12-28
forum: General Help
---

### Post by mechgt on 2012-12-28
So I have a 2GB SD card (typically used for my camera).  I tried using it for my new Raspberry Pi (install automatically reformats/partitions/etc) and now it's being reported as a 1GB card (967MB).  GParted says 1GB, fdisk -l says 1GB, Windows sees it as 1GB...

Any idea how to recover an SD card back to the proper size of 2GB?

I've been using it for years as a 2GB card (and it came from a local retail store), so I'm 99.999% certain that it's not a fake that was maliciously labeled as 2GB.

---

### Post by spynappels on 2012-12-28
any chance you can post the output of ```
df -h
``` with the SD card inserted in the reader? 
The reason I ask is that some RaPi installers actually create 2 partitions on the card, one of which will probably be formatted in ext3/4 and won't be visible in Windows.

The output above may show more than 1 partition and will give a starting point for checking what location the card is mounted at.

---

### Post by Luigi2012SM64DS on 2012-12-28
Did you see any unallocated space in GParted?
If you did then right-click on the 1gb partition and change the size to its full size.

---

