---
title: "failing disk how to recover /home partition"
date: 2015-01-28
forum: General Help
---

### Post by Neill_R on 2015-01-28
I have a failing disk below is an output from testdisk 
but things are getting worse

 8 L Linux                74120  34 27 117909 153  4  703477760 [Home_64_Server]

is what i would like to backup/clone 

where to go to get the best advise.

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER [EMAIL="grenier@cgsecurity.org"]<grenier@cgsecurity.org>[/EMAIL]
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33    25 126 37     407552 [SYSTEM]
 2 P HPFS - NTFS             25 126 38 41197 192 19  661432320
 3 P HPFS - NTFS          119957  88  4 121601  80 63   26410416 [RECOVERY]
 4 E extended             41197 192 20 117909 153  4 1232375808
 5 L Linux Swap           42045  97 37 43332 242 46   20684800
   X extended             45078   0  1 59824 204 28  236907370
 6 L Linux                45078  13 56 59824 204 28  236906496 [Desktop_12_04]
   X extended             59824 204 29 73944  53 29  226828288
No ext2, JFS, Reiser, cramfs or XFS marker
 7 L Linux                59824 236 61 73944  53 29  226826240
 7 L Linux                59824 236 61 73944  53 29  226826240
   X extended             74120   0  1 117909 153  4  703479928
 8 L Linux                74120  34 27 117909 153  4  703477760 [Home_64_Server]





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
 [Quick Search] >[ Backup ]
           Save current partition list to backup.log file and proceed

---

### Post by Bucky Ball on 2015-01-28
You could try [Clonezilla]("http://clonezilla.org/").

---

