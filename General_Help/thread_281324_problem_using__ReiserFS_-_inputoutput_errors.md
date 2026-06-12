---
title: "problem using  ReiserFS - input/output errors"
date: 2006-10-20
forum: General Help
---

### Post by merkk on 2006-10-20
Hi all,

I'm trying to format a partition using ReiserFS but i am having a problem. Its a segate baracuda 160gb sata

i used fdisk to delete the existing partitions on the drive (sdb) and then created a partition on sdb1 using the entire drive. 

I used mkreiserfs to format /dev/sdb1

i then rebooted and did 
mkdir /testdir
mount /dev/sdb1 /testdir

when i ran mount it said it was mounted using reiserfs

I then copied a few files to that directory. And then i tried doing an ls on that directory and thats when i had problems. After waiting a while i got and input/output error. The HD activity light stayed lit the whole time and even when i tried to reboot the light stayed lit and the system kept repeating an IO error for sdb every minute or so.

can someone tell me what i did wrong and how i should create a reiserfs partition and mount it? 

i also ran reiserfsck --check /dev/sdb1 and it didnt come up with any errors.

thanks

---

### Post by cd-r80 on 2006-10-27
Just terminated succesfully copying & resizing reiserfs partitions to a new hd using newest Gparted live cd. One by one. Grub made problems.

---

### Post by merkk on 2006-10-27
yeah i got it working using gparted as well.

i think my problem was a missing disk label since thats one thing i didnt do anything with and gparted complained about the lack of label and helped me set one.

---

