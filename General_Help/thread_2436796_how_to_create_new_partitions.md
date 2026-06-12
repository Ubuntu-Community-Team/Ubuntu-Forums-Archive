---
title: "how to create new partitions ?"
date: 2020-02-13
forum: General Help
---

### Post by anje2 on 2020-02-13
I have installed ubuntu 19.10 alongside Windows 10 .
now I want to get rid of the window completely .

my Q/ is , I have 2 drive on my win (C ) & ( E ) 
C / used for window 10 to be installed on .
E / I keep saving my personal files such as ( photos , videos , ... etc ) on it .

now I want  to install ubuntu all along on my laptop .
I have 2 steps : -

1. erase disc and install ubuntu.
2.something else .

so , if I use step one it will only erase the windows 10 on (C) drive and my files on ( E ) drive and it will install Ubuntu on ( C) automatically?

in case if I use step two , can I delete partition ( C ) and ( (E ) and recreate new one ? 

/---------------------------------/

what if I want to delete C and E completely 
and create 1 drive to install only ubuntu on 
and 1 drive to keep my personal files on 
and 1 drive to keep books , courses .... other things .
??? how to do that ?

---

### Post by yancek on 2020-02-13
If you already have Ubuntu installed with windows and both are working, you can simply format the windows system partition (C drive) but you will need to know which partition it is.  Linux doesn't use drive letters so you will need to know which partition is shown as the system partition from windows.  If you don't know which it is, you can open a terminal in Ubuntu and run this command and post the output here and someone should be able to tell you which is.  The Erase disk option will delete all the partitions and install Ubuntu so you need to use the Something Else option so that you don't overwrite the data partition.

---

### Post by anje2 on 2020-02-13
> **yancek said:**
> If you already have Ubuntu installed with windows and both are working, you can simply format the windows system partition (C drive) but you will need to know which partition it is.  Linux doesn't use drive letters so you will need to know which partition is shown as the system partition from windows.  If you don't know which it is, you can open a terminal in Ubuntu and run this command and post the output here and someone should be able to tell you which is.  The Erase disk option will delete all the partitions and install Ubuntu so you need to use the Something Else option so that you don't overwrite the data partition.

actually I want to install fresh ubuntu .
so I would like to format it from beginning ,
so I want to know how to delete all partition in my laptop 
and create only 2 drive , 1 for ubuntu to be installed on and 1 for saving my files on . that's all

---

### Post by mastablasta on 2020-02-13
> **anje2 said:**
> 
what if I want to delete C and E completely 

select: [COLOR=#000000]erase disc and install ubuntu.

[/COLOR]```
and create 1 drive to install only ubuntu on 
and 1 drive to keep my personal files on 
and 1 drive to keep books , courses .... other things .
??? how to do that ?
```

for this you need to select **something else**.

then create root /  - about 30-40GB should do. this is OS partition like C in windows. file system ext4
then create /home partition - this is data partition - kind of like my documents, but it will really hold all user data - file system ext4 for starters (BTRFS or ZFS will give the option of snapshots) 

depending on install type (UEFI or MBR) you might need to create EFI (for UEFI type) at the start of disk. - should be at least 512 MB.

i also add a smaller /swap partition (formatted swap) approximately the size of RAM, however this is actually no longer needed as swap file can be used instead.

you can still create more partitions later on if you have the need. it's the same in windows but in linux you don't usually need to defragment the drive before doing it. for example i added partition called /data (ext4). to create another partition later on gparted tool is used.

---

### Post by anje2 on 2020-02-13
> **mastablasta said:**
> select: [COLOR=#000000]erase disc and install ubuntu.

[/COLOR]```
and create 1 drive to install only ubuntu on 
and 1 drive to keep my personal files on 
and 1 drive to keep books , courses .... other things .
??? how to do that ?
```

for this you need to select **something else**.

then create root /  - about 30-40GB should do. this is OS partition like C in windows. file system ext4
then create /home partition - this is data partition - kind of like my documents, but it will really hold all user data - file system ext4 for starters (BTRFS or ZFS will give the option of snapshots) 

depending on install type (UEFI or MBR) you might need to create EFI (for UEFI type) at the start of disk. - should be at least 512 MB.

i also add a smaller /swap partition (formatted swap) approximately the size of RAM, however this is actually no longer needed as swap file can be used instead.

you can still create more partitions later on if you have the need. it's the same in windows but in linux you don't usually need to defragment the drive before doing it. for example i added partition called /data (ext4). to create another partition later on gparted tool is used.



thanks mate this helped :)

---

### Post by Impavidus on 2020-02-13
As nobody mentioned it and it seems to confuse you, a partition is not a drive. Windows calls a partition a drive, which is terribly confusing. You don't create drives (unless you work for Toshiba or Western Digital or whatever); you buy them and put them into your computer. But you can create partitions.

The option to erase the disk and install Ubuntu will erase the entire disk with all its partitions that Windows calls disks and make a new partition for both your operating system and your personal files. If you want to separate them, partition manually. And of course, this will delete all files.

---

