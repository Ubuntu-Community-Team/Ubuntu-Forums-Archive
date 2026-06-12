---
title: "grub error 22 can't boot any os"
date: 2008-04-01
forum: General Help
---

### Post by flugo on 2008-04-01
Please be patient i am new to all this. I had a dual boot of winxp and ubuntu going just fine but in the original install of ubuntu I some how managed to make 7 different partitions -- 3 of which were unused. Both OS's booted and worked just fine but in tinkering around with ubuntu; i was uninstalling some programs from the synaptic package manager and screwed ubuntu up. it would boot up to the log in screen but would go no further. so i decided , since i wanted to reclaim some of the partitions that were'nt being used, i would delete them all ( except the windows partition) and start over with a fresh install of ubuntu with newly created partitions. 

I am now understanding just how much i don't understand anything about creating and deleting partitions.  in the disk management of XP,i deleted the partitions including the one that contained ubuntu and grub. I got an error msg in the process that said i could not go any further in the delete because the partition was being used. so i beleive i have a partial deletion of grub. the boot process still defaults to grub but stops with an error 22. Now i can't boot into XP -- I can however get into the windows setup menu but i AGAIN do not know what i am doing. 

Following what we  will loosely call logic now , I assume i need to some how disable grub so the windows bootup will take over. then take care of the partitioning and then reinstall ubuntu but i am open to suggestions, instructions or even a reprimand or two. I am in the ubuntu live cd at the moment and i looked at the gparted program but am unsure how to proceed . 

        thanks

---

### Post by zvacet on 2008-04-02
>  I can however get into the windows setup menu

If you can do that then type fixmbr (or fix mbr) and that should be it.If you don´t have luck with it try with [SuperGrubDisc.](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

