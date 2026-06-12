---
title: "USB Partition confusion"
date: 2008-06-01
forum: General Help
---

### Post by arunjayaseelan on 2008-06-01
I partitioned a USB drive with 750MB for FAT32 and the rest for ext2 for installing Ubuntu on USB..  Now i want to use this drive for Windows again.

I tried fdisk and deleted the 2 existing partition.  and created a new one (took the default size).  it can only create one partition of 716MB.   fdisk shows a total of 2012MB (its a 2GB drive).

but when i fdisk is shows only one partition of 716 MB.  When i try to create a new partition, i get the message "no more sectors available"   Someone please help.

---

### Post by didac on 2008-06-02
Can you post the listing of

```
sudo fdisk -l
```

---

### Post by arunjayaseelan on 2008-06-04
Disk /dev/sdb: 2012 MB, 2012217344 bytes
63 heads, 62 sectors/track, 1006 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1006     1964687    6  FAT16


When i try to create a new partition, i get the following message:

root@arun-laptop:/home/arun# fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 2012 MB, 2012217344 bytes
63 heads, 62 sectors/track, 1006 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1006     1964687    6  FAT16

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
No free sectors available

Command (m for help):

---

### Post by arunjayaseelan on 2008-06-04
Previously it had a primary FAT32 partition of 715MB and another Primary ext2 partition of about 1.2GB.

I Deleted the 2 partitions but now I am only able to create a primary partition of 716MB.  Please help.

---

### Post by didac on 2008-06-05
Sorry, maybe I'm too drowsy today, but I see the partition you created is already using the whole disk. You have 1006 cylinders total and that's what is being used. Try

```
df -h
```

to see whether that's right.

Have you already formatted the partition with mkfs.vfat?

---

### Post by arunjayaseelan on 2008-06-05
But the first line of the output shows 2012MB available. 
I am a newbie to linux/unix.  Still figuring my way through the OS, try my best to stay away from MS.  

Can you please tell me what the df command should show me.  or how i should use it on the usb drive.  Once I get home I will try the man pages on df (which if i remember right should be disk free).  I will post the out put... Thanks for helping.

---

### Post by KingTermite on 2008-06-05
When you deleted the other partition, did you issue the "w" command to write the new partition table?

---

### Post by didac on 2008-06-05
> **arunjayaseelan said:**
> But the first line of the output shows 2012MB available. 
I am a newbie to linux/unix.  Still figuring my way through the OS, try my best to stay away from MS.  

Can you please tell me what the df command should show me.  or how i should use it on the usb drive.  Once I get home I will try the man pages on df (which if i remember right should be disk free).  I will post the out put... Thanks for helping.

Open a terminal and type the df -h The option -h means "readable in human form" with Mb and Gb, not with blocks.

My output shows:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              19G  5.5G   12G  32% /
varrun                252M  212K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   84K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             108G   48G   61G  44% /media/sda1
/dev/sdb3              19G  1.6G   17G   9% /media/sdb3
/dev/sdc1             2.0G  882M  1.1G  45% /media/disk

```

/dev/sdc1 is a USB flash I inserted.

If you don't use any switches, df will look less 'human readable':

```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             19222656   5663616  12582468  32% /
varrun                  257920       212    257708   1% /var/run
varlock                 257920         0    257920   0% /var/lock
udev                    257920        84    257836   1% /dev
devshm                  257920         0    257920   0% /dev/shm
lrm                     257920     34696    223224  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1            112639712  49516160  63123552  44% /media/sda1
/dev/sdb3             19248416   1653424  17594992   9% /media/sdb3
/dev/sdc1              2011268    902648   1108620  45% /media/disk

```

---

### Post by arunjayaseelan on 2008-06-08
My USB is /dev/sdb  When i issue df -h  I cannot even see the drive:

root@arun-laptop:/home/arun# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G  3.1G   48G   7% /
varrun                625M  104K  624M   1% /var/run
varlock               625M     0  625M   0% /var/lock
udev                  625M   52K  625M   1% /dev
devshm                625M   12K  625M   1% /dev/shm
lrm                   625M   38M  587M   6% /lib/modules/2.6.24-18-generic/volatile


But when I do df on the usb drive specifically I get this.

root@arun-laptop:/home/arun# df -h /dev/sdb
Filesystem            Size  Used Avail Use% Mounted on
udev                  625M   52K  625M   1% /dev

the file system says udev.... it is confusing.  I think I did not use w to write the partition table after I deleted the 2 partitions.  Now how can I fix this problem?

---

### Post by arunjayaseelan on 2008-06-08
I deleted the only partition that existed. and then I used w to write to the partition table. now again if I do a fdisk, this is what I see.

Disk /dev/sdb: 2012 MB, 2012217344 bytes
62 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System


It still shows me only 1022 cylinders.  What should I do.

---

### Post by didac on 2008-06-08
It's not yet partitioned. Do it again. Type:

```
sudo fdisk /dev/sdb
``` 

Type in order:
n => to create a new partition
p => to make it primary
1 => to be sdb1

Use the whole area, and make it partition type 83 (ext3) or b (windows vfat for compatibility in other computers without Linux)

w to exit writing changes.

Then fdisk -l should show you sdb1. If it keeps on showing sdb without the digit 1, something went wrong.

Well, it's partitioned, but you have to format it now. Do a

```
sudo mkfs.ext3 /dev/sdb1
```

or a 

```
sudo mkfs.vfat /dev/sdb1
```

if you prefer a windows partition. (advisable)

---

### Post by arunjayaseelan on 2008-06-10
It worked.  Thanks to all for your prompt help.

---

