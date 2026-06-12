---
title: "help mounting ntfs"
date: 2006-12-19
forum: General Help
---

### Post by God.Jr on 2006-12-19
ok my problem is , well i think caused by ***_:evil: windows:evil: _***.......](*,) 
well i shutdown windows yesterday and installed ubuntu as i was getting sick of restarting my pc 5 times a day.......

well now the problem is wen i try to mount my ntfs,sata, drive and it won't mount......
i think the problem is the fact that window crashed when i shut it down and it never finished checkin my drives and unmounted it from there, so they are sitting unchecked at the end and now ubuntu doesn't want anything to do with them.....:-k 
my friend suggested i try find a program  to do this so that ubuntu can read it.....or if anyone can give any suggestions that could help

i really need this drive it has everything n it, i think i'm using an IDE drive to run ubuntu as ubuntu seems to like those drives a lot more than my sata drive, which has given me more trouble than anything 

**_any and all help is appreciated_**

---

### Post by amd-64 on 2006-12-19
It is unlikely that the crashed ntfs drive is causing this problem. Can you post your /etc/fstab and the command are you using to mount the ntfs volume. Also post the output of "mount"

---

### Post by God.Jr on 2006-12-24
thanx for the help but i figuered it out.........
i reinstalled windows and shutdown widows three times and it read my drives.....so now i have them showing up on linux...

thanx though

---

