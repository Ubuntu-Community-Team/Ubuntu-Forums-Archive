---
title: "The Good, The Bad And The Ugly 3 Different Partitions"
date: 2007-12-18
forum: General Help
---

### Post by Joeblackberry on 2007-12-18
OK.... Guys and (of course( Dont want to voilate any Feminist Rule) Girls. Start to Laugh!

I´ve bought a new Notebook and i installed Ubuntu 7,10 and it runs bumbastic fantastic!!!! I choose the automatic partition mode and i choose 50% ubuntu and 50% free because i wanted to install windows too 

Now i have 3. not 1... not 2... but 3 partitions how can this happen?

Names of the Partitions or "discs"

1.FD_BETA9SR2 wich has in it like FREEDOS.BSS INSTALL:LOG  FDBOOTCD:ISO etc.. (59,6 GB)

2.DATA wich has nothing there (53,6 GB)
3. DATEISYSTEM (SYSTEM) (30.3 GB)

Where should i Install Windows? 

or what should i do ????

Thx a lot

---

### Post by r-mo on 2007-12-18
Ubuntu would normally create 3 partitions I think (I always do manual partitioning) 
1 for ubuntu
1 for swap
1 free space

but I'm somewhat confused by the partitions that you're reporting as it certainly wouldn't make swap 30GB.  Can you post the output of the command

```
sudo fdisk -l /dev/sda
```

assuming /dev/sda is your hard disk (it normally is)

---

