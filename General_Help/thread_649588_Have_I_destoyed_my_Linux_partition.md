---
title: "Have I destoyed my Linux partition?"
date: 2007-12-25
forum: General Help
---

### Post by DarkLoki on 2007-12-25
Hi, I have been using Ubuntu for a while and have been very happy with it. A few months ago I also installed Ubuntu on the new pc of my parents and that turned out to be great.

But unfortunately there were still some problems, they have a camera that I have not been able to get working on Linux and my sisters have to use stupid software from school that is windows only. So I decided to turn the pc into a dual boor with XP. I wrote down all the information to get grub working again and statted the windows setup. But it seemed there was something wrong, it showed the 160gb harddrive as an 140gb partition. I was afraid that it only showed the linux partition and it was messing with it I stoped the setup. It already seemed that grub was dead as the computer would just give a black screen. I booted the live cd to setup grub again but it did not work.

It seems that the xp setup destroyed the linux partition. Fdisk lists only one partition as a fat16 one and when I startup the partition manager it will crash after showing 140gb unallocated space.:mad:

Does anyone know what is going on? I am still pretty new to linux but I really hope I can recover the pc as it contains a lot of stuff from my parents.

Can anyone help?

---

### Post by LaRoza on 2007-12-25
Can you see data with a live disk? If not, the partition was lost.

Although recovery is possible, it is most likely not worth the trouble (and time and knowledge) needed. I hope there are backups available, as they should be made whenever installing an OS or altering the partition table.

---

### Post by Sef on 2007-12-25
using the live cd, let's check the partitions to see what is there.

Applications > Accessories > Terminal

then type this code  ```
sudo fdisk -l
``` (Small L)

paste the results here.

Depending on what happened the information may all, in part, or not at all be there.

---

### Post by meierfra on 2007-12-25
Click on testdisk in my signature.

---

### Post by DarkLoki on 2007-12-26
Great to see some answers,

This is the result from fdisk:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
86 heads, 15 sectors/track, 242311 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      208090   134217727+   4  FAT16 <32M

```

sda1 should have been the linux partition, I wanted to leave some spcae for for instance windows so i made the linux partition 140gb. So I did not think it was a big deal to just install it in the still unpartitioned space.

Using the live cd i cannot see the files. I will take a look at the testdisk a bit further but it looks like a program that could save me. Got to burn another livedisk with it i guess.

---

### Post by meierfra on 2007-12-26
> Got to burn another livedisk with it i guess.

You can install it do the Ubuntu Live CD 

```
sudo apt-get install testdisk
```

---

### Post by DarkLoki on 2007-12-27
Yes you are right, and so I did. Testdisk immediately listed my linux partition and I was verry happy to see it listed all the files :). It seemed that the windows installer wrote a fat16 partition to the table overlapping my old and did not not work out ofcource. I deleted the fat partition, restarted the livedisk and was happy to see all the files again. Just had to get grub working again and the pc worked again like nothing has happend :).

Thank you for your help guys! and especially meierfra for the program that saved me :)

---

