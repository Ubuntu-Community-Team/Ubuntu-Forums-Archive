---
title: "Problems with partitions after using LVPM"
date: 2007-11-25
forum: General Help
---

### Post by palaciodeinvierno on 2007-11-25
Hi. This is my problem: I installed Wubi 7.04 on my computer (Vaio, 512ram). Then I migrated to Ubuntu using LVPM. No problem so far.

The thing is that before migration I prepared the partitions with Norton Partition Manager running in windows. I created one for windows (17g) and there is a 5gigas partitions for Windows recovery. I left the rest (18gigas) "not allocated", to allow LVPM to do the Ubuntu installation.

THE PROBLEM is that now I have something like 10gigas that I cannot allocate to either partitions (ext3 linux or NFTS windows). I've tried to run Partition Manager from Ubunto (rev 26) but I can't find it anywhere in applications, and it doesn't shows up when I reboot (it shows 6 different options, 3 for ubuntu and 3 for windows).

Do I need a different program? What can I use to resize my linux partition using the free space?

Thanks a lot in advance

---

### Post by Joon Lee on 2012-11-20
So I assume you are trying to partition from Ubuntu.
Sometimes a  partition manager does not show up as a menu option. However, it might  still be installed. Open up a terminal (if you can't find a menu option for that either try Ctrl-Alt-T) and type in "sudo gparted" without the quotes.
See what happens.

---

