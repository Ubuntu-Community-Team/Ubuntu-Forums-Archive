---
title: "a very special boot problem help needed"
date: 2007-07-02
forum: General Help
---

### Post by regine's on 2007-07-02
Hallo all
I do have a bit special system:p
2 dual Opterons and lot's of memory
first (primary)disk, Grub is here, is Debian with my scsi disk array outside the box Cinarella and Jahshaka :KS
First(secondary) disk is Ubuntu for everything else, mail, openoffice and else;)
Secondarty slave will be Windows, have to have it for PageMaker 

Now as the first disk is no Windows disk, 
there is masterboot sektion made by rescue XP fixmb and makeboot and grub is there

how to boot Windowx...XP :(
anyway SWAP is a SCSI within the box for all Linux

---

### Post by regine's on 2007-07-03
it is so stupid

title Windows XP
root (hd2.0)
savedefault
makeaktive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


what for
on the Winwos disk ther is NO Grub it is plain vanilla Windows
can be updatet when ever it chrashes or what else
it can be taken out and start alone as disk 1 in the system
so it can be updatet with a Windows CD rejupered and voila

Start disk is an old connor formated mit a Win98 Floppy
and fixmbr and fixboot runnig over
so this Grub can start what ever it will never sitting on any OS Disk:KS

---

