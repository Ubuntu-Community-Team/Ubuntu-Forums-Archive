---
title: "help to edit the disk partition on ubuntu lvm codes or gparted ??"
date: 2015-05-11
forum: General Help
---

### Post by fbio7 on 2015-05-11
Hi. I'm using the ubuntu 15.04

I would like to create a partition on my disk to put some personal files. I don't know how to do it. 

What I'm thinking about is get the partitioning to follow:
Device     Boot  Start       End   Sectors               Size Id Type
/dev/sda1  *      2048    499711    497664           243M 83 Linux
/dev/sda2       501758 976771071 976269314   465,5G  5 Extended
/dev/sda5       501760 976771071 976269312   165,5G 8e Linux LVM
/dev/sda6                                                            300,00 8e Linux LVM

------------------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------------------

**Today** in my pc there are two partition and a logical volume mount in the sda2 (sda5)
Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 976771071 976269314 465,5G  5 Extended
/dev/sda5       501760 976771071 976269312 465,5G 8e Linux LVM

what I already do. 

1)I installed gparted and tried to resize the  /dev/sda5 but the system only permit to get 52 MB free to resize. (image 01 )

[ATTACH=CONFIG]261910[/ATTACH]
image 01

2) I saw the logical volumes mounted.. can I resize the logical volume root mounted to create free space and add a new logical volume using lvm ?? is It the best way to get a partition to put my personal files??

~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                YeRLS9-19Yw-IDHP-gkfP-KszR-1v33-RXc1pR
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2015-05-01 15:42:55 -0300
  LV Status              available
  # open                 1
  LV Size                463,73 GiB
  Current LE             118714
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                Aghz3K-FRxW-5zoo-oZEQ-2h4n-z9Xm-c4Fm5q
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2015-05-01 15:42:56 -0300
  LV Status              available
  # open                 2
  LV Size                1,74 GiB
  Current LE             446
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

**please someone can help me  ???**

ps: sorry for the mistakes in the write my english is not the best

---

### Post by nerdtron on 2015-05-11
(I replied to this thread a few minutes ago. It seems that my comment was deleted when the threads were merged?)


Anyway, I'll type again.

As things can get complicated on LVM, do you have any reason to use it? I can see that you only have a single hard drive and unless this is a shared computer, it's likely that you'll need to resize partitions frequently. So I'd recommend that you just partition normally, no LVM.

Partitioning something like: 
/boot - 500MB
/ - 50GB (for the OS and apps)
/media/my_stuffs - the rest of the hard drive, put all you personal files here. (custom mount point)

---

### Post by cariboo on 2015-05-11
please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by fbio7 on 2015-05-11
Hi...Nerdtron

 how can I ability a change on the size of partition /dev/sda5...did you see the image 01 above I had problem to edit the size with gparted, the system only permited that 52 mb free to put on unallocated space

you can help me with the commands to partition normally??

---

### Post by oldfred on 2015-05-11
You normally do not create another LVM, but another partition inside the LVM.
And gparted does not work on LVM, only the partitions the LVM is in. 

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)


 LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)

---

### Post by fbio7 on 2015-05-14
Hi ...thanks for the tips.

I read some links and decided partitioning the HD using gparted. I saved my personal files on a backup memory card, burned a cd of gparted live and changed the partitions (format the hd).

The central idea was create a partition to put my personal files so in the next time that I format my pc I won't format this partition. (the logical partition /dev/sda6 )

sudo fdisk -l
Device     Boot     Start       End   Sectors   Size             Id Type   (mount point)
/dev/sda1  *         2048    499711    497664   243M          83 Linux   (/boot)
/dev/sda2          499712   4595711   4096000     2G         82 Linux swap / Solaris  ( )
/dev/sda3         4595712 976773119 972177408 463,6G   5 Extended  ( )
/dev/sda5         4597760 546693119 542095360 258,5G   83 Linux       (/)
/dev/sda6       546695168 976773119 430077952 205,1G  83 Linux     (/home)

I hope this answer help someone  :) !!!

---

### Post by oldfred on 2015-05-14
Glad you resolved it.

Just be sure to use Something else and include /home in new install, but DO NOT tick the format box or it will erase the data in /home.

---

