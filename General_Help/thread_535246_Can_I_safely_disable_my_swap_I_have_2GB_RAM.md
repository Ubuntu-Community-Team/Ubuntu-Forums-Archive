---
title: "Can I safely disable my swap? I have 2GB RAM"
date: 2007-08-26
forum: General Help
---

### Post by QwUo173Hy on 2007-08-26
I've noticed that only 1 of my 2 GB of ram is usually in use. Ubuntu made a 5GB partition of swap space. Only 33MB of this is ever in use. Would there be an advantage to disabling swap space? (besides the disk space I could salvage).

---

### Post by astralsin on 2007-08-26
i wouldnt disable it but you sure don't need 5gb swap space.  you could turn your swappiness down to 0 and repartition to give yourself about 64mb swap space.  that'd increase performance and give you some disk space back.  read this for more info [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

---

### Post by notwen on 2007-08-26
I also have 2gb of swap which is rarely ever used, but until I need the HDD space I doubt I'll ever remove it.  As far as your question goes, yes you can disable swap.  Just open gParted (sudo apt-get gparted) and once in gParted simply unmount it and reduce or completely remove your swap partition, but as stated before unless you need the space, I wouldn't be too concerned. Good luck. =]

Quote from a random website.

> 
Swap space in Linux is used when the amount of physical memory (RAM) is full. If the system needs more memory resources and the physical memory is full, inactive pages in memory are moved to the swap space. While swap space can help machines with a small amount of RAM, it should not be considered a replacement for more RAM. Swap space is located on hard drives, which have a slower access time than physical memory.

Swap space can be a dedicated swap partition (recommended), a swap file, or a combination of swap partitions and swap files. 

The size of your swap space should be equal to twice your computer's RAM, or 32 MB, whichever amount is larger, but no more than 2048 MB (or 2 GB).


---

### Post by QwUo173Hy on 2007-08-26
Thanks guys. I switched swappiness to 0 and resized the partition to 128MB (just to be safe). I'm much happier now :)

---

