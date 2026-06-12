---
title: "[SOLVED] im an idiot"
date: 2008-01-05
forum: General Help
---

### Post by minibeardeath on 2008-01-05
so yeasterday i decided to install ubuntu on a spare hdd i had left over from a recent RAID problem. my current xp drive is a 500gb RAID 1 array, and in order to install ubuntu on the secondary (third physical) hdd i thought i would need to set the bios into ide mode. my problem is that GRUB was installed on the windows mbr. so now when i want to start up windows the bios has to be in RAID mode for the hdds, but GRUN is unable to access the linux disk so instead of anything booting up i just get a black screen that says "GRUB" and will not respond to anything i try to type. i am currently running of a tirtiary (fourth physical) hdd that i loaded w/ xp (but due to liscensing i only have 11 days left till i have to reinstall this disk). all the files are fully accessable on the RAID 1 array from the active hdd but i cannot boot from that disk. i would like to know if i can access and edit the mbr from the good hdd, or if i can simply re-install xp on the  corrupted disks (if possible w/o losing all the data). lastly, i dont know if GRUB was written to the mbr of both disks in the RAID 1 array or just one. thanks for the help. 


btw. im running ASUS commando mobo.
2 Samsung hd501lj for the RAID 1
1 samsung hd501lj for the linux drive
and some WD 160gb for the third hdd.

---

