---
title: "MBR &amp; Boot Record"
date: 2013-01-24
forum: General Help
---

### Post by nethompson on 2013-01-24
I'm a little stumped about this. I've search online and found nothing so I'm hoping I can get some help from here. I was recently looking at my MBR and Boot Record on my mechanical harddrive which is currently running 64-bit Ubuntu. The starting C/H/S for the MBR is 20 21 00 (80 20 21 00 07 FE FF FF 00 08 00 00 00 00 00 05). I was under the impression that the starting C/H/S was typically 01 01 00.

Also, the total number of sectors between the MBR and the Boot Record have thrown me for a loop. The total sectors in the MBR is 00 00 00 05 (83886080) and the total sectors in the Boot Record is F0 FF FF 04 (83886064) which is a 16 sector difference. I always thought that there was a 1 sector difference between the two.

MBR:

80 20 21 00 07 FE FF FF 00 08 00 00 00 00 00 05

Boot Record:

EB 52 90 4E  54 46 53 20   20 20 20 00  02 08 00 00
00 00 00 00  00 F8 00 00   3F 00 FF 00  00 08 00 00
00 00 00 00  80 00 80 00   F0 FF FF 04  00 00 00 00
00 00 0C 00  00 00 00 00   02 00 00 00  00 00 00 00

---

### Post by oldfred on 2013-01-24
I not sure what the question or answer is.

But drives have not used CHS since hard drives went over 8GB. They use LBA or large block allocation or large setting in BIOS.

In fact we find issues from both Windows and testdisk which still internally use CHS and write extended partitions end beyond the last sector as they incorrectly round CHS values back.

       Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

    
       Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.

---

### Post by nethompson on 2013-01-24
Okay, from what I understand now is that those bytes, located at the c/h/s offsets, are no longer being used, correct? If that's true, why would they have changed the way they did? I know that the new starting sector of a disk is located at 2048 instead of 63 but why is there a 16 sector difference between the total number of sectors on the volume instead of 1?

---

### Post by nethompson on 2013-01-24
Okay, I did some looking around and I found some links within your links that helped me with the c/h/s offsets and values. This link: [http://thestarman.pcministry.com/asm/mbr/W7MBR.htm#INTRO](http://thestarman.pcministry.com/asm/mbr/W7MBR.htm#INTRO) helped me tremendously on how the c/h/s offsets and values relate to the starting sector of the partition (2048). My other question still remains about the sector differences though.

---

### Post by oldfred on 2013-01-24
Is it a new 4K drive?
       [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?tit](http://ubuntuforums.org/showthread.php?tit)'s 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by nethompson on 2013-01-24
No, this drive was made in 2008 and the sectors are 512 bytes each according to fdisk -l.

---

