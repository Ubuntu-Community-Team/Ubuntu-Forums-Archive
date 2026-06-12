---
title: "issue with partition EXT4 while data structure is visible under Windows/Linux"
date: 2020-07-26
forum: General Help
---

### Post by alain.roger on 2020-07-26
Hi,

i have a 2.5 HDD with 2 partitions / mounting points.
Under Ubuntu 20 and windows 10, the file structure (files / directories) are visible and can be browsed.
However when i want to move or copy data to another mounting point, i can not as I/o error message raises or some files are copied but not the whole.

Before displaying error message about I/O, ubuntu 20 informed me about some superblock error. However a fsck did not help and while before i had really few badblocks, now fsck says the whole disk (both mounting points) are 100% badblocks.

Disk seems ok and i guess some metadata/superblock are messed up so system is confused. However data structure is 100% visible and can be browsed.

What can i do to retrieve data as i purchased another SSD to migrate data ?

any idea ?

thx

---

### Post by dinkidonk on 2020-07-26
Need more info..

1) 2 partitions, but which file systems?
2) Windows / Ubuntu, but which system was the culprit?

If the file-systems are EXT4 and they have been damaged from Windows, they may be unrecoverable as a whole. But even if the file-system has been borked, the files them selves may be recoverable with a file carver.

First thing to do - Keep the drive away from Windows! Optimally you would make a disk image to work with instead of working with the drive itself. Now, in Linux install [TestDisk/PhotoRec]("https://www.cgsecurity.org/wiki/TestDisk"), and try to fix the drive with TestDisk (read the Step By Step guide carefully). If that does not succeed, you can try to carve the drive with PhotoRec in order to recover the files (again, read the Step By Step carefully first). This usually works quite well if there is no hardware damage.

---

### Post by alain.roger on 2020-07-26
1. Basically both partitions are in EXT4
2. problem happened under Ubuntu 20.04 on my laptop (as the HDD is my laptop HDD it is under ubuntu 20.04) and i checked if i can see data under windows (with some recovery tools) and under ubuntu with testdisk... both OS can see data but it seems that superblocks got wrong without any reason

i'm currently testing:
```
[FONT=monospace][COLOR=#000000]sudo e2fsck -b 32768 /dev/sdi1[/COLOR][/FONT]
```[FONT=monospace]

it takes time to complete as my HDD is 2 TB

[/FONT]

---

### Post by dinkidonk on 2020-07-27
Do you know why it happened? Power loss or something? You might also want to check the S.M.A.R.T. data on the drive to see if there are indications of a hardware failure.

---

### Post by alain.roger on 2020-07-28
I have no idea why it happened... i guess the standard issue for HDD... some bad sectors... but HDD is less than 3 years old :(

no i'm trying the 8th possible superblock address with e2fsck... i will review tomorrow morning results...

---

