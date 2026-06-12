---
title: "unable to mount location"
date: 2013-12-20
forum: General Help
---

### Post by ahmedo047 on 2013-12-20
There are two HDD (sda and sdb) on my computer. I installed ubuntu 12.1 on "sda". And I mounted to /home "sdb". Desktop-->above menu bar-->Go-->Computer-->2.0 TB Hard Disk(sdb)-->Unable to mount location.
I want to access "2.0 TB Hard Disk(sdb)" from there (Go-->Computer). How can I mount it?

physics@physics:~$ sudo mount /dev/sdb5 
mount: /dev/sdb5 already mounted or /home busy
mount: according to mtab, /dev/sdb5 is already mounted on /home

**I typed "fdisk -l" on terminal:**
```
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000072a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480585727   240291840   83  Linux
/dev/sda2       480587774   500117503     9764865    5  Extended
/dev/sda5       480587776   500117503     9764864   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001ca53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2046  3907028991  1953513473    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sdb5            2048  3907028991  1953513472   83  Linux
```

---

### Post by steeldriver on 2013-12-20
the 'mount' output is telling you that /dev/sdb5 is already mounted at /home - you can't mount it twice

what exactly is the issue? can you not access your user's home dirs?

---

### Post by ahmedo047 on 2013-12-20
sudo umount -l /dev/sdb5
cd /media
sudo mkdir hdd 
sudo mount /dev/sdb5 /media/hdd
The problem is solved by above commands.

---

### Post by ahmedo047 on 2013-12-20
My computer has two HDD (named sda and sdb). I installed ubuntu 12.1 on sda (first HDD). And I mounted to /home sdb (2TB Hard Disk, second HDD). Desktop-->Up menu bar-->Go-->Computer-->2TB Hard Disk

I got this warning "Unable to mount location".

I typed  ```
sudo fdisk -l 
```on terminal:

  Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000072a0

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 480585727 240291840 83 Linux
/dev/sda2 480587774 500117503 9764865 5 Extended
/dev/sda5 480587776 500117503 9764864 82 Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001ca53

Device Boot Start End Blocks Id System
/dev/sdb1 2046 3907028991 1953513473 5 Extended
Partition 1 does not start on physical sector boundary.
/dev/sdb5 2048 3907028991 1953513472 83 Linux 
```

sudo umount -l /dev/sdb5
cd /media
mkdir hdd 
sudo mount /dev/sdb5 /media/hdd
```

Now I can be able to access the sdb (2 TB HDD). But there are two folder "physics" -includes document, downloads... and "last+found" in sdb HDD.
**I dont want to any files related to ubuntu there (sdb). That is, it must be empty. And  I should be able to access it. I will use it (sdb) for storing files. **

I think I will reinstall the ubuntu 12.1 on sda "first HDD".  Which mount point should I select for sdb "second HDD"? 
Choices:
/media, /boot, /home ...

---

### Post by oldfred on 2013-12-20
When you installed did you make sdb5 /home or are you attempting to mount it as /home now.
You can only mount any partition once. Normally /home is installed inside / (root) but can be on a separate partition.
But /home includes all your settings and user configurations. It also has your data folders like Music, Documents, etc and some hidden folders where Firefox or Thunderbird have their profiles (data & settings).

I prefer to install to a smaller system partition of 10 to 25GB and keep /home inside /. But then I use links to mount all the folders from my data partition into /home. You can do the same by mounting each folder into fstab also which some others suggest. I do this primarily because I have several 25GB / partitions with different installs and want the same data mounted in all of them.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by tfrue on 2013-12-20
I would put the /boot on your faster drive. /media is used for mounting drives in linux, so if you plugged in a USB, it would probably mount under /media. So, of the three, I would put /home on the second drive, but if it were me, I would create a new mount point like "/files/whatever" and make that my primary drive for holding files. If you are going to be saving stuff to your Desktop, the I would certainly put /home on the second drive. 

I think your idea of reinstalling would probably be a good idea just because it's always easier starting over. Usually. Anyway, certainly format your second drive by using fdisk.
So let's being. Please type:
```
sudo fdisk /dev/sdb
```
Then delete the partitions that are on the drive, type:
```
d
1
d
5
```
So that should've deleted both of the partitions on the /dev/sdb drive. Now we need to create a new partition, type:
```
n
p
[enter]
[enter] # I want to note that in one of these choices it will ask you to define the ending block number, so you make the partition as large or small as you want here. Only want to use 1000GBs? type +1000GB. Other wise, it's going to use the entire drive.
[enter]

```
Now we need to define the type of file system the partition will use. If you want to use linux, the type "**83**", If Window's NTFS, type "**7**"
Then type "**w**" to write the changes!

Now let's make a file system on our new partition, begin by typing:
```
sudo mkfs.ext4 /dev/sdb1
```
It will probably run for awhile since it's 2TB, but you should have the second HDD ready for Linux!

Then just reinstall and format the /dev/sda drive and mount what ever directory you wish on any drive!

Good luck,
Chris

---

### Post by tfrue on 2013-12-20
> prefer to install to a smaller system partition of 10 to 25GB and keep  /home inside /. But then I use links to mount all the folders from my  data partition into /home. You can do the same by mounting each folder  into fstab also which some others suggest. I do this primarily because I  have several 25GB / partitions with different installs and want the  same data mounted in all of them.
That is mighty impressive oldfred. I wish I had the space to do such things, and I will here very soon!

---

### Post by ahmedo047 on 2013-12-23
The problem doesnt still resolved :(
```
physics@physics:~$ sudo fdisk -l

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000072a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480585727   240291840   83  Linux
/dev/sda2       480587774   500117503     9764865    5  Extended
/dev/sda5       480587776   500117503     9764864   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001ca53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2046  3907028991  1953513473    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sdb5            2048  3907028991  1953513472   83  Linux
```

```
physics@physics:~$ sudo fdisk /dev/sdb

The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): d
Partition number (1-5): 1

Command (m for help): d
No partition is defined yet!

Command (m for help):
```

physics@physics:~$ sudo mkfs.ntfs /dev/sdb5
/dev/sdb5 is mounted.
Refusing to make a filesystem here!

---

### Post by tfrue on 2013-12-23
.Alright, so you have a few technical errors here. I will show you an example. ```
chris@tfrue:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1813033f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1109764095   554677248    7  HPFS/NTFS/exFAT
/dev/sda3      1109764096  1237694463    63965184   83  Linux
/dev/sda4      1237694464  1250263039     6284288   82  Linux swap / Solaris

Disk /dev/sdb: 31.4 GB, 31449415680 bytes
32 heads, 32 sectors/track, 59985 cylinders, total 61424640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    61424639    30711296    7  HPFS/NTFS/exFAT
chris@tfrue:~$ 

```
The /dev/sdb is my USB. It has one partition, /dev/sdb1, that starts on block 2048, and ends on 61424639, and the type of that partition is NTFS. So the whole drive is being used for one partition as NTFS. So I want to edit the whole drive rather than the partition, so we type:
```
chris@tfrue:~$ sudo fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 31.4 GB, 31449415680 bytes
32 heads, 32 sectors/track, 59985 cylinders, total 61424640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    61424639    30711296    7  HPFS/NTFS/exFAT

Command (m for help):
``` 
I'm using 'p' to print the partitions on the drive, which it finds the one that was listed during the fdisk -l command. We now want to delete the partition, and create a new primary one and since I only have one partition it will auto select to delete it, but I would select 5 in your case, then 1. So type:
```

Command (m for help): d  #**To delete the single partition on the drive, there is only one so it chose it automatically.**
Selected partition 1

Command (m for help): p

Disk /dev/sdb: 31.4 GB, 31449415680 bytes
32 heads, 32 sectors/track, 59985 cylinders, total 61424640 sectors     
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

   Device Boot      Start         End      Blocks   Id  System       #**To show that we successfully deleted the partiton****.**

Command (m for help): n    #**We want a new partition.**
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1 #** From here to--**
First sector (2048-61424639, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-61424639, default 61424639): **--Here, just press enter.**
Using default value 61424639

Command (m for help): p

Disk /dev/sdb: 31.4 GB, 31449415680 bytes
32 heads, 32 sectors/track, 59985 cylinders, total 61424640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

   Device Boot      Start         End      Blocks   Id  System      #** Just showing that we created a new partition that will use the entire drive and a file system type of Linux.**
/dev/sdb1            2048    61424639    30711296   83  Linux

Command (m for help): t  #** Since I want to use NTFS, type 't' for type.**
Selected partition 1
Hex code (type L to list codes): 7 #** 7, is the hex code of NTFS, you can press 'l' to list all the hex codes and associated file system types.**
Changed system type of partition 1 to 7 (HPFS/NTFS/exFAT)

Command (m for help): p

Disk /dev/sdb: 31.4 GB, 31449415680 bytes
32 heads, 32 sectors/track, 59985 cylinders, total 61424640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    61424639    30711296    7  HPFS/NTFS/exFAT  #** Just to show that the type has changed from Linux to NTFS.**

Command (m for help):w #** type 'w' to write the changes, and give it time to finish, which it will let you know when it is, and then we will make a file system for the drive.**

```

Now lets begin making the file system. Type:
```
sudo mkfs.ntfs-3g /dev/sdb1

#** If that doesn't work, try this, and I'm also assuming that you chose to create the new partition as 1, instead of anything else**

sudo mkfs.ntfs /dev/sdb1
```

---

### Post by ahmedo047 on 2013-12-23
There is not "ntfs".

```
Command (m for help): l

 0  Unassigned       4  SunOS usr        8  SunOS home      82  Linux swap     
 1  Boot             5  Whole disk       9  SunOS alt secto 83  Linux native   
 2  SunOS root       6  SunOS stand      a  SunOS cachefs   8e  Linux LVM      
 3  SunOS swap       7  SunOS var        b  SunOS reserved  fd  Linux raid auto
```

---

### Post by tfrue on 2013-12-23
Make sure that you have the ntfs package by typing:
```
sudo apt-get install ntfs-3g
```
If you haven't in while, it might be a good idea to 
```
sudo apt-get update
```

---

### Post by tfrue on 2013-12-23
It also may help to upgrade to the newest release, 13.10

---

### Post by ahmedo047 on 2013-12-24
I applied your 9th reply(Alright, so you have a few technical errors here. I will show you an example.....)
And the problem is solved. You are wonderful.Thank you very much.

---

### Post by tfrue on 2013-12-24
No problem friend! Glad I could help.

Chris

---

### Post by tfrue on 2013-12-24
Don't forget to mark this thread as solved, so others will know!

---

