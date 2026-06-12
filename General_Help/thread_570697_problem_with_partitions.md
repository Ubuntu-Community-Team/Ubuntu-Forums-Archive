---
title: "problem with partitions"
date: 2007-10-08
forum: General Help
---

### Post by 870881 on 2007-10-08
Hi
I bough a half pc, which doesnt work with my old windows HD (its on old HD i used to install windows there, Dont know why it doesnt work anymore), Now i created a new Partition from my other HD, This Partition is now Partition no. 2, but when i try to install windows now  (I want to have windows beside ubuntu, lapidate me ;) ), and say him to install it on the second partition it gives me an error beacause he wants to write the bootsectors on Partition no 1, what is impossible (it doesnt like the format). beacaus I dont want to lose all my files, im trying to swap those partitions, can anyone help me?
before i forget: i dont have any other hard disks to save my files there, I can not delete them

sry if there are mistakes im from germany

Thank You
Uli

---

### Post by dabl on 2007-10-08
I don't think Windows can write its boot info to any other partition -- there is only 1 MBR on that hard drive, and that is where Windows must write the boot data.

You might try booting your Windows CD in "recovery mode", and then try the command line commands

"fixmbr"

and/or

"fixboot"

:)

---

