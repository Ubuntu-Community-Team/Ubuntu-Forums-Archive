---
title: "Resizing HD with 2 ntfs partitions"
date: 2015-10-26
forum: General Help
---

### Post by gaston-verhulst on 2015-10-26
Hello ,
On my computer I have 2 Harddisks, one with Xubuntu, another with Windows Vista installed.
Now, I like to resize the Windows HD.
```
gastonv@gastonv-MS-6712:~$ sudo fdisk -l /dev/sdb
[sudo] password for gastonv: 

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000440c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    20482874    10241406    7  HPFS/NTFS/exFAT
/dev/sdb2        20482875    66055247    22786186+   7  HPFS/NTFS/exFAT


```
On /dev/sdb1 I have installed Windows Vista.
In my Ubuntu linux Toolbox Book I have read something about parted and ntfsresize commands.

Please my question:
1. Can I remove the /dev/sdb2 partition, so that only one partition of 33.8 GB remains?
2. If not, can I reduce /dev/sdb2 to a mininum, so that I can expand the /dev/sdb1 to a maximum size e.g. 30 GB ?

Many thanks in advance for helping.
Kind regards,
Gaston Verhulst

---

### Post by dragonfly41 on 2015-10-26
Are these two hard drives /dev/sda and /dev/sdb actually inside your computer or is /dev/sdb an external drive?

Reason I ask is because I have Vista and Ubuntu 14.04 setup to dualboot in my local /dev/sda
but I thought that Vista (or Windows in general) cannot boot from an external hard drive.

---

### Post by Vladlenin5000 on 2015-10-26
Hi and welcome.

*** Do NOT resize Windows partitions with anything else than WINDOWS tools. ***

1. ??? What is in that partition? If it isn't the partition where your Windows is installed and just a data storage partition then certainly you can remove it without issues and then expand the first partition.
2. You can also do that, of course.

All in all, you make no sense. Why ask about something that's up to you to decide? And considering that all you want to do is Windows related and - again - should be done from Windows, if you need further instructions I suggest you check Windows docs, forums, etc. And, of course, Google is your friend.

Do you have any question regarding Ubuntu/Linux?

---

### Post by Vladlenin5000 on 2015-10-26
> **dragonfly41 said:**
> Are these two hard drives /dev/sda and /dev/sdb actually inside your computer or is /dev/sdb an external drive?

Answer in the OP's first sentence:
> On my computer I have 2 Harddisks, one with Xubuntu, another with Windows Vista installed.

And no, you can't install Windows in an external drive.

---

### Post by gaston-verhulst on 2015-10-26
Hello,
Thanks to all for your replies.
In fact they are 3 hard drives inside an old PC.

```
gastonv@gastonv-MS-6712:~$ sudo fdisk -l

Disk /dev/sda: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20005650 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00040429

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    10008494     5004216    c  W95 FAT32 (LBA)
/dev/sda2        10008576    11032575      512000   83  Linux
/dev/sda3        11032576    20004863     4486144   8e  Linux LVM

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000440c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    20482874    10241406    7  HPFS/NTFS/exFAT
/dev/sdb2        20482875    66055247    22786186+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002a695

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    58597375    29297664   83  Linux
/dev/sdc2       157992958   160086015     1046529    5  Extended
/dev/sdc3        58597376   157990911    49696768    b  W95 FAT32
/dev/sdc5       157992960   160086015     1046528   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/vg_gastonv-lv_swap: 2113 MB, 2113929216 bytes
255 heads, 63 sectors/track, 257 cylinders, total 4128768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


```
In the past, I had Win98 and Fedora on it.
Because of problems I installed Xubuntu on it as a dual system with Win98 and with GRUB I could select one.
Because I liked to install Windows Vista instead of Win98, with gnome-tools I formatted /dev/sdb1 and /dev/sdb2 to NTFS, that is needed for Vista.
After that I could install successfully Vista on /dev/sdb1, but now I like to expand that partition and/or resize or delete the second partition /dev/sdb2.

Please how can I rearrange that /dev/sdb?
When needed I can reinstall Windows Vista any time.

Now, with GRUB menu, by starting up, I can select either Xubuntu or Windows Vista.

Again many thanks in advance,
Kind regards,
Gaston Verhulst.

---

### Post by coffeecat on 2015-10-26
Use Vista's inbuilt Disk Management tool to delete or shrink sdb2, and then to enlarge sdb1. My advice is not to use a 3rd party Windows-based partitioning tool. Some are prone to corrupting the partition table in such a way that doesn't prevent Windows, or Ubuntu, from running, but does confuse Linux-based partitioning tools. Which may cause problems for you later when working in Xubuntu. I myself have been a victim of this.

---

### Post by gaston-verhulst on 2015-10-26
Thank you very much for the hint, I will try to do it in Vista.
Greetings,
Gaston Verhulst.

---

### Post by dragonfly41 on 2015-10-26
If your problem is shortage of space in sdb1 there is one possible approach you can try without resizing sdb2.

In Vista directory look for pagefile.sys   (in my installation it is 3 GB in size).

You can set it to zero size and reboot Vista to create a new page file.

You might also try running pagefile.sys in sdb2 partition.

[http://superuser.com/questions/701094/how-can-i-shrink-my-12gb-pagefile-sys](http://superuser.com/questions/701094/how-can-i-shrink-my-12gb-pagefile-sys)

---

### Post by gaston-verhulst on 2015-10-26
Hello to all of You,

The problem is solved.
Many thanks for the splendid communication and the good tips.
In Windows Vista in Computer management > Disk management I could remove /dev/sdb2 and expand /dev/sdb1 to the whole disk capacity.

```
gastonv@gastonv-MS-6712:~$ sudo fdisk -l /dev/sdb
[sudo] password for gastonv: 

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000440c4
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    66052922    33026430    7  HPFS/NTFS/exFAT

gastonv@gastonv-MS-6712:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sdc1       28706812 3936084  23289464  15% / >> Xubuntu
none                   4       0         4   0% /sys/fs/cgroup
udev              502972       4    502968   1% /dev
tmpfs             102596     992    101604   1% /run
none                5120       0      5120   0% /run/lock
none              512968      84    512884   1% /run/shm
none              102400      24    102376   1% /run/user
/dev/sdb1       33026428 9889028  23137400  30% /media/gastonv/2CD55D585FD832C6 >> Windows Vista
/dev/sdc3       49684608 8527424  41157184  18% /media/gastonv/8798-8892


```
Kind regards,
Gaston Verhulst.

---

