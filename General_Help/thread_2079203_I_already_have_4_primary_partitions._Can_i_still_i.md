---
title: "I already have 4 primary partitions. Can i still install ubuntu?"
date: 2012-11-01
forum: General Help
---

### Post by vikash_chandola on 2012-11-01
I recently bought hp pavilion g6 2016. It comes with preinstalled windows 7 home basic , a recovery drive and 2 other drives. unfortunately all these primary partitions. so i can not make any more drives using disk management.
when i install ubuntu, Usually i make a new drive (using disk management) and install ubuntu using wubi in that drive(newly created). By doing so i can access all the drives except the drive in which i have installed ubuntu. Now i can only install ubuntu on C(windows) drive. If i do so then i will not able to access all of my documents videos sngs etc. and installation will gets useless...
so i though to make regular install from CD/DVD but i want to know in which kind of drive ubuntu(primary or logical) is installed. If it is logical then OK! but if it is primary then windows may show any problem because in that case there became 5 primary partitios!! and windows hates 5 primary partitions.

so this is full scenario i want to know
Is it possible to access C drive even after installing ubuntu(wubi)?
In which kind of partition ubuntu installe(logical/primary)d if installed through CD/DVD/USB?

if u have any other suggestion then please tell me.

---

### Post by jerome1232 on 2012-11-01
It's not that Windows hates 5 primary partitions, it's that with the MBR style partition scheme, it's not possible to have more than 4 primary partitions.

Anyways, I found a work around when I ran into this problem with my netbook, there is a tool that can convert primary partitions into logical partitions but to do this you have to have your boot files for windows 7 on a separate partition from the C: drive, can you provide a screenshot of the windows disk management utility showing your partitions so that I can better help you?

---

### Post by Cheesemill on 2012-11-01
There is no need to create a seperate partition for Ubuntu when using Wubi. The whole point of Wubi is that you can install Ubuntu without repartitioning your drive.

The contents of the drive that Ubuntu is installed on are always available in the /host directory.

---

### Post by oldfred on 2012-11-01
Whatever you do, do not create partitions in Windows. It will convert to dynamic partitions which are not compatible with Linux and even some Windows repair tools.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by hal8000 on 2012-11-01
A wubi install uses your windows NTFS partition so you can install it as long you have free space. 
Wubi uses your NTFS partition, which will defrag and take longer to load and wont give you the same performance as an install on dedicated linux partitions.


Most hard drives have an Intel partition table, which only allows 4 primary partitions. To create more partitions, one of the primary partitions must become an extended partition (which will hold all the logical drives in the extended section).

An output from sudo fdisk -l below:



  Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   268317629   134158783+   7  HPFS/NTFS/exFAT
/dev/sda2   *   268317630   677910869   204796620    7  HPFS/NTFS/exFAT
/dev/sda3       677910870   718860615    20474873   a5  FreeBSD
/dev/sda4       718860616   976768064   128953724+   5  Extended
/dev/sda5       718860618   718892684       16033+  82  Linux swap / Solaris
/dev/sda6       718892748   739873216    10490234+  83  Linux



You can see that primary partition4, sda4 is extended and sda5 onwards
are logical partitions. Some OS like FreeBSD can only be installed in primary partitions.


It looks as though HP may have installed windows deliberately that way on your laptop to try and prevent you installing anything else. If it was me I would email the company and ask for an explanation or tell them you wont buy from them again, as you have the right what OS you want to install on your computer.

Regarding windows, you can install from any CD, your serial number will be on a sticker underneath the machine. The recovery partition will contain some drivers that are not included with the windows install, however you be get updated driver from the HP website.
Hope that helps.

---

### Post by jerome1232 on 2012-11-01
Since everything is being thrown out there, I used MiniPartition Tool (windows based) to convert my c: drive into a logical partition and then shrunk my c drive for space.

This only works if you one of your little partitions has your boot files, which was the case for my HP Netbook.

---

### Post by vikash_chandola on 2012-11-01
> **jerome1232 said:**
> It's not that Windows hates 5 primary partitions, it's that with the MBR style partition scheme, it's not possible to have more than 4 primary partitions.

Anyways, I found a work around when I ran into this problem with my netbook, there is a tool that can convert primary partitions into logical partitions but to do this you have to have your boot files for windows 7 on a separate partition from the C: drive, can you provide a screenshot of the windows disk management utility showing your partitions so that I can better help you?
I will go for wubi installation of 12.04.
here is an image of my disk management.

---

