---
title: "Some help: Moving partition with PARTED"
date: 2008-02-24
forum: General Help
---

### Post by St0RM53 on 2008-02-24
HI! I want to move my partition /dev/sda4, but i get this error in parted:
Error: File system has an incompatible feature enabled.

I know how to use parted, and all the restrictions to it, but this is a problem i can't solve:S
i'm using Ubuntu feisty 7.0.4(LIVECD) and parted 1.7.1
Is there a fix, or using another program to do the job?

Here is the print:

Number  Start      End        Size       Type     File system  Flags
 1      63s        208844s    208782s    primary  ext3         boot 
 4      45271170s  87875549s  42604380s  primary  ext3              
 3      91184940s  92036384s  851445s    primary  linux-swap        

and what i'm trying to do:
 move 4 20844s 42813224s

If you haven't understand, i'm trying to move the partition so then i can bind it with the free space.

Any help, is welcome.

---

### Post by St0RM53 on 2008-02-25
bump! plz anyone?

---

### Post by housam on 2008-02-25
Use the new version of Gparted.you'll find it [[COLOR="Red"]_here_[/COLOR]]("http://gparted-livecd.tuxfamily.org/").it has the ability to do your tasks.

---

