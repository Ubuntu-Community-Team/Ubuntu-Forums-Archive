---
title: "PATA + SCSI disk booting problems"
date: 2008-02-03
forum: General Help
---

### Post by kUdtiHaEX on 2008-02-03
Hi people :)

I have nForce 3 based mainboard with one PATA disk (it's some Seagate 120GB) and one Hitachi SCSI disk (SCSI controller was made by Adaptec).
I've sucessfully installed uBuntu 7.1 but i'm having some trouble with GRUB.
After POST, i just receive message "GRUB" and thats it. It does not want to boot but if i put Live CD and selcet "boot from the 1st hard drive" option, it works normally and my ubuntu, after 2 minutes, is up.

But if i remove SCSI drive, it works fine? I have 3 partitions on the PATA drive (boot, swap and /) and one on SCSI drive which is NTFS with static data (nothing important and nothing that should mess with GRUB). 

"find /grub/stage1" returns hd0,0 as result which is correct. So, what is the problem? :(

---

