---
title: "HDD &gt; Showing incorrect storage information &gt; storgage amount remaining &gt;"
date: 2023-07-22
forum: General Help
---

### Post by noobtechninja on 2023-07-22
Hi there guys.

I was hoping that you could help me out with a strange issue that I've just
discovered.

**Background / History:**
I have an external HDD drive (a WD 4 TB unit)
I have recently, deleted all partitions on it, created 1 partition,
reformatted it as ext4 then transferred about 700 GB of data onto the HDD


**Issue:**
The external HDD now appears to be showing the incorrect amount of available
storgate left.

1. Using Dolphin 
WD-HDD: (total) available size = 1.6 TiB
WD-HDD: spaced used = 621.4 GiB

2. Using Kparted =
WD-HDD: (total) available size = 3.64 TiB
WD-HDD: spaced used = 621.75 GiB

Which I would consider to be correct


3. Using the CLI =

```
/dev/sdd1     1.7T    622G    945G    40%    /media/(my username)/wd_backup_02
```

3.1. Here it is again, in a bit more of an easier to read format
```
/dev/sdd1 
[size] 1.7T
[used] 622G
[available] 945G
[used] 40%
```

Which (again) I would definitely consider to be incorrect.


**Questions:**
1. Why would the system be showing this disparity / incorrect usage on Dolphin,
but correctly using Kparted ?

2. How can I rectify this ?

TIA for any help or advice


Useful information:
HDD = WDC WD40EXRX-00SPEB0 (Western Digital)
OS: Ubuntu 22.04 LTS
Kernel version: 5.19.0-46-generic (64-bit)
Plasma version: 5.24.7

---

### Post by MAFoElffen on 2023-07-22
I don't use the GUI for statistics, because each seems to interpret things 'differently' if I want to know, I use the cli, and just see how Linux itself see what is there. For example
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,fsused,fsuse%,mountpoint
NAME   LABEL       SIZE FSTYPE FSUSED FSUSE% MOUNTPOINT
sda                1.8T                      
&#9500;&#9472;sda1 {SYSTEM}    550M vfat    31.4M     6% /boot/efi
&#9500;&#9472;sda2             128M                      
&#9500;&#9472;sda3 {Windows}   900G ntfs                 
&#9500;&#9472;sda4             983M                      
&#9500;&#9472;sda5              30G                      
&#9492;&#9472;sda6           931.4G ext4   673.5G    74% /
sdb                1.8T                      
&#9492;&#9472;sdb1 SSD2        1.8T ext4                 
sdc                1.8T                      
&#9492;&#9472;sdc1 mSATA2      1.8T ext4   952.7G    52% /mnt

```

---

### Post by oldfred on 2023-07-22
Typical of using old MBR(msdos) partitioning, not gpt partitioning. MBR was created in the 1980's when MB was large & GB was unheard of, so made max of 2TB to last forever. 
Or now you converted drive to 2TB by using MBR.

Fdisk, or parted will show partition type.
sudo fdisk -lu
sudo parted -l

One line will say this gpt or dos.
[FONT=monospace][COLOR=#000000]Disklabel type: gpt
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]Partition Table: gpt[/COLOR]


[/FONT][FONT=monospace][COLOR=#000000][/COLOR]



[/FONT]

---

### Post by TheFu on 2023-07-22
Many file systems reserve 5% of the storage so it can only be used by root.  In the says of 100GB disks, that would be 5GB - not too much, but with 4TB, that becomes 200GB!  

The good news is that using **tune2fs**, an admin can set the reserved blocks to a smaller number/percentage.  I leave it at 5% for OS-related partitions, but I don't let any of those be allocated over 35G or so.  For purely data areas, I set the reserved areas to 0%.  the point of the reserved space was to allow a little room for root processes to keep going even when file systems are really full.  Unix systems will crash when OS file systems are full.

I'm ignoring that there are different drive units depending on the software used.  For example 1,000GB is 1TB according to HDD makers, but 1024GB is 1TB according to software makers.  It is the difference between *GB* and *GiB* in textbooks.  So, if you want to see how large your 4TB disk really is, remember that 1KB is 1024B and do the divisions.

Formatting does use some space. inodes are pre-allocated to hold all the files the file system will ever be able to hold for the life of that file system.  At the time of format, we can specify the number of inodes reservered to better fit our specific needs.  I've run out of inodes a few times, but typically only with smaller file systems that were under 20GB.  For example, if we look at the reserved/used inodes first, then the blocked used:
```
$ \df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/vda1      464000 331165 132835   72% /
/dev/vda2      154128  55479  98649   36% /var/www

$ \df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/vda1      ext4      7.1G  3.1G  3.7G  46% /
/dev/vda2      ext4      2.3G  900M  1.3G  42% /var/www

```
I created those file systems over a decade ago and actually had to add more storage for /var/www because the file system ran out of inodes. It wasn't about storage. It was about zero inodes available.  That website is built using thousand and thousands of tiny files. Each file eats an inode.

Just some things to be aware about.

I never trust GUI tools to provide facts when it comes to storage stuff.  We never really know what the programmer was thinking or where they get the data or how much they might round it.   Advanced file systems don't always show the correct values for df/du either, so beware.

---

