---
title: "[SOLVED] can't find hard drives.. existing threads didn't help.."
date: 2008-04-08
forum: General Help
---

### Post by Dr.Ninethousand on 2008-04-08
hi, making another thread because sudo fdisk -l doesn't show my other drives, as it seemed to for others with similar problems..

I installed Hardy on a new HDD and attached my former boot drive (jumper set to 'slave')..  at first it showed up, although unmounted, and was easily mounted with a double click and a password..  I moved my /home to the new OS drive..  now I've also attached my other old storage drive, with the plan of moving all stored data to the new drive, reformatting the old ones, and moving it back..  however, now the older drives don't show up at all..

```

rick@Kutulu:~$ sudo fdisk -l
[sudo] password for rick:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fe68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1278      498015   82  Linux swap / Solaris
/dev/sda3            1279        2494     9767520   83  Linux
/dev/sda4            2495       60801   468350977+  83  Linux
rick@Kutulu:~$                                                
```


edit: 

sda1 = /
sda2 = swap
sda3 = /tmp
sda4 = /home

---

### Post by Dr.Ninethousand on 2008-04-08
:lolflag:

well I had two drives on one IDE ribbon and both set to 'slave'..   :p


so that was the problem..  funny what basic things you can go years without knowing..

---

### Post by dcstar on 2008-04-09
> **Dr.Ninethousand said:**
> :lolflag:

well I had two drives on one IDE ribbon and both set to 'slave'..   :p


so that was the problem..  funny what basic things you can go years without knowing..

Please mark as Solved.

---

### Post by Dr.Ninethousand on 2008-04-09
oh I see, there's a button for that..  heh, I edited the title at least..

---

