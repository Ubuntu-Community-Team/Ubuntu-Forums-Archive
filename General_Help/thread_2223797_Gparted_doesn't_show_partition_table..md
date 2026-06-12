---
title: "Gparted doesn't show partition table."
date: 2014-05-12
forum: General Help
---

### Post by rizos on 2014-05-12
Gparted wont show any partition table, it shows 500gb of unallocated space even i have a dual boot win7/ubuntu 12.04.

how can i make gparted recognize the partition table as it is?

this is the output of sudo blkid:


```
/dev/sda1: LABEL="System Reserved" UUID="6A7ACF807ACF4811" TYPE="ntfs" 
/dev/sda2: UUID="38A6D1F9A6D1B798" TYPE="ntfs" 
/dev/sda3: UUID="6a1b491f-bbd0-4bd4-8c21-f761af3795d8" TYPE="ext4" 
/dev/sda6: UUID="bdffe4ca-caf0-4a89-90c0-86be4c6e28ac" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="ba43e92f-b2c2-4f26-a542-e73e22fadbad" TYPE="swap"
```

and this is what fstab file shows:

```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=6a1b491f-bbd0-4bd4-8c21-f761af3795d8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=344dcb85-5421-446c-9758-886fa0afbcb0 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


# /home on /dev/sda6 after installation
UUID=bdffe4ca-caf0-4a89-90c0-86be4c6e28ac /home           ext4    defaults        0       2

```

i recently reinstall ubuntu 12.04 and forgot to have sda6 as home, also i forgot to encrypt the directory now when i try i dont have enough space, i manage to recover all of my files but it shows im using 120gb of space on home directory, but some files now are duplicated is there a way to create a new home directory encrypted and move all of my files into the new partition without an external hard drive?

---

### Post by sydney2 on 2014-05-13
Hello There
Well it seems the partitioning table might be corrupted. In cases where U convert from mbr to gpt in windows (Win PE) and vice versa these might indicate like this when it comes to linux disk utilities like gparted. Try printing the partitioning table with parted or gnu-fdisk if it is the same issue. As for Your home directory problem I can' t help. 

Sydney

---

### Post by rizos on 2014-05-13
thanx sydney, what means printing the partitioning exactly?, i dont get what should i do, could you explain bit more so i can understand which direction em i heading. 


Z

---

### Post by sydney2 on 2014-05-13
Well as I spoke earlier printing the partitioning table. That would mean to get a layout of all the patitions on the disk. Do one thing open parted at terminal 
> #parted /dev/sd(Your disk) 
& type print. See the results. 
Next as for gnu-fdisk you need to install it so apt-get install gnu-fdisk then 
> gdisk /dev/sd(Your disk) then type print or p

I hope so U understood

Sydney

---

### Post by coffeecat on 2014-05-13
@rizos, gparted will show unallocated for the whole disc if there are certain partition table irregularities, as sydney2 said. But there is a simpler way of showing the relevant information without installing anything. Post the output of this terminal command:

```
sudo fdisk -l
```



@sydney2, point of information. Parted output will not show us the information needed. We need sector information for the drive and each partition - fdisk provides this.

---

### Post by rizos on 2014-05-13
@thamx a lot coffeecat, this is the output.



```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e7edf66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   467413872   233603512+   7  HPFS/NTFS/exFAT
/dev/sda3       467415040   498135039    15360000   83  Linux
/dev/sda4       498135078   976784129   239324526    f  W95 Ext'd (LBA)
/dev/sda5       498137088   508377087     5120000   82  Linux swap / Solaris
/dev/sda6       508379136   976771071   234195968   83  Linux

Disk /dev/mapper/cryptswap1: 5242 MB, 5242880000 bytes
255 heads, 63 sectors/track, 637 cylinders, total 10240000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf66c57fa

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

---

### Post by coffeecat on 2014-05-13
@rizos, here is your problem:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="#FF0000"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e7edf66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   467413872   233603512+   7  HPFS/NTFS/exFAT
/dev/sda3       467415040   498135039    15360000   83  Linux
/dev/sda4       498135078   [COLOR="#FF0000"]976784129[/COLOR]   239324526    f  W95 Ext'd (LBA)
/dev/sda5       498137088   508377087     5120000   82  Linux swap / Solaris
/dev/sda6       508379136   976771071   234195968   83  Linux


```

I've highlighted the problem figures in red. The end of the extended partition is showing as outside the physical boundary of the actual drive - which is, of course, an impossibility. This occasionally happens after using some Windows partitioning software and testdisk can sometimes do this if you use testdisk to recover lost partitions. Do either of these apply to you?

That's all theoretical anyway, because the fix is the same and is straightforward. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Download and install fixparts, read the instructions carefully and you should be OK.

---

### Post by rizos on 2014-05-13
was more an issue with testdisk recovering my partition table, i re install ubuntu 12.04 but i forgot to enable home directory and all my files are there but im not able to recover the account.


now with your advice i manage to have gparted recognize the partition, now funny fact is that my home folder is 120 gb of use cause old file are there, how can copy old file to the new account?.


here is how the out put of sudo fdisk -l:


```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e7edf66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   467413872   233603512+   7  HPFS/NTFS/exFAT
/dev/sda3       467415040   498135039    15360000   83  Linux
/dev/sda4       498137087   976771071   239316992+   f  W95 Ext'd (LBA)
/dev/sda5       498137088   508377087     5120000   82  Linux swap / Solaris
/dev/sda6       508379136   976771071   234195968   83  Linux

Disk /dev/mapper/cryptswap1: 5242 MB, 5242880000 bytes
255 heads, 63 sectors/track, 637 cylinders, total 10240000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e06888b

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```


what you rekon is best to do so i can copy the old files into the new account or the account istelf.

---

### Post by coffeecat on 2014-05-14
I think I follow you. One of the Linux partitions is your old home partition. When you reinstalled, you forgot to reuse the old home partition, so now your home folder in the new installation is in your root partition. Have I got that correct? 

You have two Linux partitions, sda3 and sda6, which are approx 14GB and 218GB respectively. My guess is that sda3 is your root partition and that sda6 is your old home partition. If that is so, simply moving files from a 218GB partition to a 14GB partition would not be feasible if you had more than a few GB of files in the old home partition. If my assumptions are correct, you have two options:

1 - Set up the old home partition as your home. That could be quite fiddly but doable. If the UID of your old home is different from your current UID that would add a layer of complexity but again is solvable. If your account in the old installation was the first created one, and your account in your new installation is the first created one, then the two UIDs would be the same.

2 - Use the old home partition as a data partition and get into the habit of not using your home folder for anything but small files. This would be easier to set up. Again different UIDs could be a complicating factor but also easily solvable. 

Whichever you choose, you would be better off starting a new thread, but post back with your thoughts and I can tell you what information you need to include in a new thread so that people can help you.

---

### Post by rizos on 2014-05-14
sda3 is the partition where ubuntu is installed, sda5 is where the home directory old and new is.


so old files and new files are in sda5, but i only can access the old files with sudo ecryptfs-recover-private command.


sda3 is the root (where ubuntu 12.04 is installed) and is 14 gb, but what i need is to recover the old files in to the new home partition which as a mater of fact is the same sda5.


em i been clear, sorry for the mess.

---

### Post by coffeecat on 2014-05-14
> **rizos said:**
> sudo ecryptfs-recover-private command.

I missed that your old home partition was encrypted, so what I said in my previous post is not right. Apologies.

Since we've solved your partition table problem and now moved onto what is a different issue, the best thing would be to start a new thread with a suitable title. A fresh thread is more likely to attract new helpers, and the title for this one won't attract those who can best help you. Make sure you have the word encrypted in your thread title. Good luck.

---

### Post by rizos on 2014-05-14
thanx a lot...

---

