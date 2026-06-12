---
title: "Help with going from Dual-boot 2 single boot on a IBM ThinkPad(Z61t)"
date: 2008-03-24
forum: General Help
---

### Post by GGates on 2008-03-24
I have a dual-boot setup, and now I need just Win XP for work. 

This is my problem I can not restore MBR with a Window install cd because it states that it can not see the HDD when I press -R to enter recover section.

I do not know any other way to restore the MBR without the past described method.

Is there any other way to restore the MBR?

My ideas:

This is my basic HDD situation using the Disk Management tool in Windows.

Volume                    File System     Status                                    Capacity     Free Space    %Free
(Blank)                     (Blank)            Healthy (Unknown Partition)  196MB        196MB            100%
(E: )                           (Blank)           Healthy                                    48.63GB     48.63GB         100%
IBM_PRELOAD (C: )   NTFS             Healthy(System)                      37.95GB     3.07GB            8%
IBM_SERVICE           FAT32           Healthy(EISA Configuration)   6.36GB       828MB             12%


This is what I was thinking, I said to myself what if I leave the grub in control and just reformat the linux partition (E: ) , however, I do not know if this will delete the grub.  Where is the grub installed?

Please help as you can see I basically have run out of space on my Windows partition.

---

