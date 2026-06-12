---
title: "Recover data after installing ubuntu alongside windows"
date: 2015-03-25
forum: General Help
---

### Post by Gian_Lorenzo_Spiss on 2015-03-25
I have attempted installing Ubuntu 14.04 (64bit) alongside Windows Vista on one of my old HP desktop. I have erroneously set the new windows partition way too small, leading to a corrupted NTFS drive that won't boot neither windows nor ubuntu.

I was left with an allocated NTFS partition of ~125GB and some unallocated free space where ubuntu should have been place for the remaining of the disk ~155GB.

I have attempted to run CHKDSK from an XP recovery disk, but I have been presented with an error (unrecoverable problems).

I have run a deeper scan with testdisk, found a large partition of the appropriate size and wrote it back. Now from Gparted I see the following:

[ATTACH=CONFIG]260898[/ATTACH]

so the memory for the original partition is back togheter but is not allocated.

Can anybody please advise me on how to proceed? My aim is to simply attempt and recover some file from this disk, therefore I do not care (too much) about make windows run again from it (if it could come as an easy byproduct so be it, but if it is easier to save the file, format the disk and install a fresh ubuntu I will take this option).

Thank you, I am fairly new to ubuntu.

---

### Post by pmi2 on 2015-03-25
TestDisk should allow you to recover files if they have not been overwritten.  Did you look at any of the examples on the TestDisk home page?

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

