---
title: "need help with partitioning on my dualboot comp"
date: 2007-05-07
forum: General Help
---

### Post by Rus the redfox on 2007-05-07
im dual boot my Ubuntu 7 fiesty and Microsoft Windows Vista RTM x86 on my computer and i want to resize (/) filesystem then create a fat32 with unused space. My drive are as follows

Drive 1 Master:
partition 1: Windows vista NTFS 170gb primary, boot

Drive 2 Slave:
partition 1: Ubuntu Ext3 primary 138gb root (\)
extended partition 2: Linux swap 2gb

i would like to resize my hd1,0 from 138gb to 40gb and use rest for a fat32 partition but i use gparted live cd and i get error then i use ubuntu linux live cd i still get error, and in dyne:bolic, and then partition suite in windows STILL error.:( 
i have heard to unmount swap with> sudo swapoff -a and i try and still get my error:mad: 
error i dont know what says i am not at my computer at the time but if you need it i can get more of the details through my email, [email]matttheamishman@mail.ru[/email].
still my new table i would like to be

Drive 2 slave:
partition 1: Ubuntu Ext3 40gb root (\)
partition 3: WIN fat32 98gb
extended partition 2: Linux Swap 2gb

Also I have heard of using NTFS in Linux with read and write i already know how to mount but my friend say you can get it write too which you know would be awsome so if anyone know it would much appriciated.
Cheers.:)

---

