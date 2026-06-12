---
title: "Brand New HD in Ubuntu - show NTSF and cannot get rid of it!"
date: 2016-03-14
forum: General Help
---

### Post by david472 on 2016-03-14
I am in the middle of trying to build a server - but this problem has to do with the Hard Drive - and the problem just doesn't seem to want to get resolved!

I have 2x1TB hard drives.  They are going to be in a RAID.  Both are new (for all intents and purposes, never been used in a windows environment).
One drive is formatted NTSF even after repeated attempts to delete, re-partition the file system.  How can I get rid of this??!?!  
I have tried (with much help from Darko), to format in using the terminal, and now I am trying using the LIVE desktop and still not luck.

1) Live Desktop, Gparted
2) Right click, delete
3) Right click , New
4) File System, Unformatted
5) Applied
6) Still NTSF

Any ideas or suggestions?

---

### Post by goofprog on 2016-03-14
Perhaps just zero out the hard drive to destroy any preformatted data on it.  I used to do this with USB drives.  It would take a while on a 1TB drive or try another hard drive utility to prep the drive for RAID.

---

### Post by Bucky Ball on 2016-03-14
Open Gparted, select the drive, 'Device> Create partition table'. That should remove any partitions on the drive.

I think you mean it is formatted in 'NTFS'.

---

