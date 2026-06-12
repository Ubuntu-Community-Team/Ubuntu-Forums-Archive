---
title: "dvdbackup works on breezy not on dapper"
date: 2006-12-17
forum: General Help
---

### Post by vayu on 2006-12-17
How do I trace a problem with dvdbackup?  

The same DVD will backup properly one machine but not on another.  They are running Breezy vs Dapper, slightly different kernels (2.6.15-25 vs 2.6.15-27) and different processors (P4 vs AMD 64 X2), and different hard drive interfaces (IDE vs SATA).

The error I get is:
libdvdread: Can't seek to block 2258170
Error reading BUP for title set 2
Mirror of Title set 2 failed
Mirror of DVD failed

PS.  The same machine has a partition on it with FreeBSD where dvdbackup works fine, so I don't believe it's the hardware.

---

### Post by x64Jimbo on 2006-12-17
What about the optical drive? try putting the breezy machine's drive in the dapper box.

---

### Post by ablewisuk on 2006-12-31
Try unmounting the DVD drive before running dvdbackup

---

