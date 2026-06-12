---
title: "Moving Home Area &amp; mounting new partition"
date: 2008-05-30
forum: General Help
---

### Post by oligray on 2008-05-30
How do i change a user accounts home area


i made a fat32 partition out of free space i left when i installed ubuntu (i forgot to do it as part of the installation) how do i make this partition mountable because i cant find out how to mount it..

once ive done this how do i move my home area to this partition

---

### Post by pointone on 2008-05-30
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by oligray on 2008-05-30
thanks but i got as far as the first box

what do i put instead of ext 3 because mine is fat 32 and it doenst work.. it just says did you mean vfat

---

### Post by oligray on 2008-05-30
dw i found out i had to put vfat then i had a problem that it couldnt find my special device or something but it was because i was puttting sda4 instead of 2 which is strange lol

---

### Post by Oldsoldier2003 on 2008-05-30
> **oligray said:**
> How do i change a user accounts home area


i made a fat32 partition out of free space i left when i installed ubuntu (i forgot to do it as part of the installation) how do i make this partition mountable because i cant find out how to mount it..

once ive done this how do i move my home area to this partition

Don't do it. FAT and NTFS do not handle Linux permissions properly and you will mess up your system if you move /home to a FAT or NTFS partition.

---

### Post by oligray on 2008-05-30
that really sucks

i was hoping to have a data partition that i could share with windows and ubuntu

meh i will sort it then :) 
thanks for warning me

---

### Post by oligray on 2008-05-30
ok now i made a extended partition with 2 logical partitions a ext3 one and a fat 32 one

becasue you cant have more than 4 primary and i had. 
1) UBUNTU
2) Linux Swap
3) Windows
4-5) Fat 32 and Ext 3

will this work

and also i cant mount these partitions... 

actually i have a sneaking suspicion as to why i have this issue. and i will give my idea a try then get back to you i am a noob but at the same time i will be fixing an issue i already have.

pleases say if i need to do something to mount these drives because i will be re installing ubuntu because it is a messs now and will be easier to start afreshh :)

lol
thanks

---

