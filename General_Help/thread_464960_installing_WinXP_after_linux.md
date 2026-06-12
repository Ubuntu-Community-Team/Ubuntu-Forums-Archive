---
title: "installing WinXP after linux"
date: 2007-06-05
forum: General Help
---

### Post by davmil2 on 2007-06-05
Hi
I installed ubuntu dapper drake and formatted my drive in the process but now have decided to reinstall windows xp then maybe set up as a dual boot.  Trouble is, no matter what i do the windows xp disk cant run (installs a heap of drivers then freezes).  I have also tried a W2000 install disk which starts up but when i try to format the drive it says it damaged or inaccessable.  I have tried using fdisk to format it as ntfs but that hasnt helped. Ubuntu still sees the drive so its not damaged, just not recognisable to windows so what happened in the ubuntu install process that has caused this problem.

---

### Post by ezrollers on 2007-06-05
you need to create a partition that is readable by windows, e.g. ntfs

Use gparted on ubuntu to resize the partitions and to create a new one.

Start windows installer, choose the partition that you've just created and it should work.

---

### Post by davmil2 on 2007-06-05
Tried that with fdisk, the xp instal disc still wouldnt go (and i have tested it on my other machine and it works fine).

I would be happy to reformat the whole drive at the moment and go back to xp then set it up for dual boot later but just cant get the xp disc to run or format the drive, even when i have formatted it as ntfs in fdisk

---

### Post by taurus on 2007-06-05
Can you post the output of this command from a terminal while you are in Ubuntu?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by davmil2 on 2007-06-05
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by taurus on 2007-06-05
```
sudo fdisk -l
```
That would be lower case letter l as in **larry**.

---

### Post by davmil2 on 2007-06-05
Thats what i used including the dash and got what you see above.  Tried without the "-" and got "unable to open l".  I probably should mention that in all this i have formatted the disk a couple of times and have nothing installed and am operating of an ubuntu live disc at the moment

---

