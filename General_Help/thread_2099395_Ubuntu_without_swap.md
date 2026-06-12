---
title: "Ubuntu without swap"
date: 2012-12-29
forum: General Help
---

### Post by elliotn on 2012-12-29
I have 4 partitions 
1. 40GB ext4 ubuntu
2. 2GB  swap
3. 100 GB NTFS win7
4. 356 GB NTFS Storage
I need an extra partition but Gparted won't allow over 4 partitions, can I remove the 2GB swap to get that extra partition I need. 

will ubuntu still work without a Swap

---

### Post by Elfy on 2012-12-29
Might - depends on how much RAM you have. 

Though I assume you are also going to be resizing partitions to get free space, unless you're making a 2Gb partition.

If that's the case - make it extended then you can create a new swap as a logical and your new partition as logical.

---

### Post by elliotn on 2012-12-29
> **Elfy said:**
> Might - depends on how much RAM you have. 

Though I assume you are also going to be resizing partitions to get free space, unless you're making a 2Gb partition.

If that's the case - make it extended then you can create a new swap as a logical and your new partition as logical.

how do I make an extended partition

---

### Post by vanadium on 2012-12-29
An extended partition is a "workaround" to allow you to have more than four partitions on your system.

In order to make it, you would need to delete existing partitions to make free space. In the free space, an extended partition can be created. In that extended partition, you can create as many partitions as you wish. At that point, they are called "logical partitions".

You have to consider if you really need your extra partition after all.

About the original question: depends indeed on the ram. Even with a lot of ram, it is not bad to have your swap as a saveguard in the (more and more unlikely) case that the extra working memory is needed anyway. Another reason might be that swap is needed for hibernation.

---

### Post by elliotn on 2012-12-29
so basically I just delete swap and resize the 350GB to maybe 200GB then I can make the remaining 150gb extended partition and then recreat swap

---

### Post by oldfred on 2012-12-29
Yes. But you have to edit partitions from a liveCD so all partitions are unmounted. You may also have to click on swap and right click swapoff as liveCD like to mount swap to speed things up.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

    
But the new swap will have a new UUID. So you will have to edit fstab with the new UUID.

       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

    sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a

---

### Post by Elfy on 2012-12-29
> **oldfred said:**
> Yes. But you have to edit partitions from a liveCD so all partitions are unmounted. You may also have to click on swap and right click swapoff as liveCD like to mount swap to speed things up.
Generally this is so - but if the op's shrinking the win partition and deleting the swap it could be done in running system - will just need to swapoff 

Regardless of where you're doing it though, I'd backup stuff in the ntfs storage beforehand.

---

### Post by elliotn on 2012-12-29
looks like complicated work so I will leave it and just wipe Win 7

thanks for your efforts

---

### Post by vanadium on 2012-12-29
> **elliotn said:**
> so basically I just delete swap and resize the 350GB to maybe 200GB then I can make the remaining 150gb extended partition and then recreat swap

Could be, but what you effectively can do depends on the actual layout of the partitions.

---

### Post by vasa1 on 2012-12-29
> **elliotn said:**
> looks like complicated work so I will leave it and **just wipe Win 7**

thanks for your efforts
I'm not sure that's a good idea. Why delete it? Instead,take some time to understand how to shrink partitions and make new logical ones as suggested.

---

### Post by Elfy on 2012-12-29
> **elliotn said:**
> looks like complicated work so I will leave it and just wipe Win 7

thanks for your efforts

sounds complicated - but once you start it's not :)

but if you're not going to do it can you mark the thread solved

---

### Post by elliotn on 2012-12-29
k guys help me do this but I just noticed that my partitions are a mess and worse fdisk /dev/sda has no option f 

  ```
 elliotn@elliotn-G31-M7-TE:~$ sudo fdisk -l
[sudo] password for elliotn: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1f1295a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4094     8605695     4300801    5  Extended
/dev/sda2   *   103540736   309622783   103041024    7  HPFS/NTFS/exFAT
/dev/sda3       309622784   976773119   333575168    7  HPFS/NTFS/exFAT
/dev/sda4         8605696   103540735    47467520   83  Linux
/dev/sda5            4096     8605695     4300800   82  Linux swap / Solaris

Partition table entries are not in disk order
elliotn@elliotn-G31-M7-TE:~$ 

elliotn@elliotn-G31-M7-TE:~$ sudo fdisk /dev/sda

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): 

```

---

### Post by elliotn on 2012-12-29
> **elliotn said:**
> k guys help me do this but I just noticed that my partitions are a mess and worse fdisk /dev/sda has no option f 

  ```
 elliotn@elliotn-G31-M7-TE:~$ sudo fdisk -l
[sudo] password for elliotn: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1f1295a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4094     8605695     4300801    5  Extended
/dev/sda2   *   103540736   309622783   103041024    7  HPFS/NTFS/exFAT
/dev/sda3       309622784   976773119   333575168    7  HPFS/NTFS/exFAT
/dev/sda4         8605696   103540735    47467520   83  Linux
/dev/sda5            4096     8605695     4300800   82  Linux swap / Solaris

Partition table entries are not in disk order
elliotn@elliotn-G31-M7-TE:~$ 

elliotn@elliotn-G31-M7-TE:~$ sudo fdisk /dev/sda

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): 

```

screenshot of Gpated

---

### Post by elliotn on 2012-12-29
BTW fdisk /dev/sda  "f" is not available

---

### Post by vanadium on 2012-12-30
Don't worry: it won't prevent your system from working.

---

