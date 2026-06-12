---
title: "Ubuntu 14.04 cannot see one ntfs partition, while it sees 2 other ntfs partitions"
date: 2014-07-24
forum: General Help
---

### Post by Chanath on 2014-07-24
After dist-upgrade, Ubuntu 14.04 cannot see one ntfs partition, even though it sees 2 other ntfs partitions (windows 8). The partition it cannot see is formatted ntfs, so it could be seen by Windows and by Linux. It contains data. 
fdisk -l sees that partition as sda3, while blkid doesn't see it at all. 
ntfs-config doesn't see that partition too.
Windows was closed correctly, that is, sda3 was unmounted before closing windows.
I need to access sda3. Could you help?
Thanks!

---

### Post by Dreamer Fithp Apprentice on 2014-07-26
Did you try manually mounting it from a command line? Like:```
sudo mount /dev/sda3 /path/to/some/empty/dir
```or if that doesn't work try with the -t option:```
sudo mount -t ntfs /dev/sda3 /path/to/some/empty/dir
```Have you looked at fstab to compare how the ones that work are listed compared to the one that doesn't?
------------------------
Afterthought:
for sda3, of course, substitute the appropriate device name. Ditto for the mythical path and directory name.

---

### Post by gordintoronto on 2014-07-26
Did you use: sudo blkid

When you say Ubuntu sees two partitions but not another, I assume you mean that when you run Nautilus (file manager) two of the partitions appear in the top-left corner as NN GB filesystem?

Can you list the partitions in your response?

---

### Post by Chanath on 2014-07-27
Nautilus doesn't see sda3, and sudo blkid too. sudo fdisk -l sees all the partitions.
This happens only in Ubuntu 14.04, but not in Zorin OS9, Deepin 2014, Ka OS (Arch), or Sabayon (Gentoo).

Neither, 
> sudo mount /dev/sda3 /path/to/some/empty/dir

nor,

> sudo mount -t ntfs /dev/sda3 /path/to/some/empty/dir

This  happened after the last dist-upgrade. I have done 2 more dist-upgrades  after that, but no success.  I have dist-upgrade in Zorin and Deepin,  and they see that ntfs partition. This is quite strange.

---

### Post by bab1 on 2014-07-27
What do you get with this command```
sudo blkid -c /dev/null -o list
```

Here is what I get (note the UNMOUNTED partition at the bottom)```

/dev/sda1          ext4                 /                      c4807753-7a09-4d0a-8052-bf96c1f81d40
/dev/sda2          swap                 <swap>                 69e4c9c7-a439-416d-85a9-c79162983068
/dev/sda3          ext4                 /home                  46a258bf-6ace-4d52-b4d7-db47e7b3de7b
/dev/sda5          LVM2_member          (in use)               RO3Frr-gU0o-LHqe-LGLG-Uem3-NKRT-fI2Ytb
/dev/sda6          LVM2_member          (in use)               eNAIr1-R1pE-Qg1S-SRUP-4YAx-tht1-xCsLrf
/dev/mapper/malibu-alpha
                   ext4      alpha      /lvm                   a56104e3-761a-483f-bca2-8c061158e9e6
/dev/sdb1          vfat      UBU_1404   (not mounted)          D047-B8FE

```

---

### Post by Chanath on 2014-07-28
> sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    System Reserved (not mounted) 085E76845E766A78
/dev/sda2  ntfs             (not mounted)  2A6CFF786CFF3D5F
/dev/sda5  ext4             (not mounted)  eb85a743-c857-486d-87e1-779c42f6b774
/dev/sda6  ext4             (not mounted)  ab381cfa-3db3-4fb5-bab4-fd76bd735f50
/dev/sda7  ext4             (not mounted)  63e64b4a-1a5b-42bd-b04d-ff8fe6c40995
/dev/sda8  ext4             (not mounted)  9d895c9e-a5c6-448b-bc96-904c6d18751e
/dev/sda9  ext4             /              9224f728-8681-4690-aa3f-e00acba7b55b
/dev/sda10 ext4             (not mounted)  5d0c66eb-d6ff-4e70-a81d-3681071023eb
/dev/sda11 swap             <swap>         636c9885-b16f-4b8d-bf1f-e77339632b60
/dev/sda12 ext4             (not mounted)  afcc1c95-c95f-4d15-b1a2-bdc437310066

As you see, the sda3 partition is not seen. This is my Data partition, which is supposed to seen by Linux distros and Windows.

---

### Post by bab1 on 2014-07-28
> **Chanath said:**
> As you see, the sda3 partition is not seen. This is my Data partition, which is supposed to seen by Linux distros and Windows.
The partition can be named something else.  The naming sda or sdb or sda1 or sda2 are only for the Linux kernel.  Let's carry on a bit.  

Post the output of these 2 commands```

cat /etc/fstab

sudo parted -l

```

[COLOR="#0000FF"]Edit:  It helps if you post the text output in the [code] blocks.  This helps preserve the formatting,   You can do that by clicking on the [SIZE=5]# [/SIZE] icon at the top of the advanced editor. [/COLOR]

---

### Post by Chanath on 2014-07-28
This is what I get;
> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=9224f728-8681-4690-aa3f-e00acba7b55b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=636c9885-b16f-4b8d-bf1f-e77339632b60 none            swap    sw              0       0
UUID=4701A4C61D83C5C4 /dev/sda3  ntfs-3g  defaults,windows_names,locale=en_US.utf8 ro  0 0

> sudo parted -l
[sudo] password for czanat: 
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs
 2      106MB   41,1GB  41,0GB  primary   ntfs            boot
 3      41,1GB  148GB   107GB   primary   ntfs
 4      148GB   320GB   172GB   extended
 5      148GB   170GB   22,8GB  logical   ext4
 6      170GB   196GB   26,0GB  logical   ext4
 7      196GB   217GB   20,9GB  logical   ext4
 8      217GB   240GB   23,0GB  logical   ext4
 9      240GB   262GB   21,6GB  logical   ext4
12      262GB   287GB   25,4GB  logical   ext4
10      287GB   317GB   30,0GB  logical   ext4
11      317GB   320GB   2718MB  logical   linux-swap(v1)

---

### Post by bab1 on 2014-07-28
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda9 during installation
UUID=9224f728-8681-4690-aa3f-e00acba7b55b / ext4 errors=remount-ro 0 1
# swap was on /dev/sda11 during installation
UUID=636c9885-b16f-4b8d-bf1f-e77339632b60 none swap sw 0 0
[COLOR="#FF0000"]UUID=4701A4C61D83C5C4 /dev/sda3 ntfs-3g defaults,windows_names,locale=en_US.utf8 ro 0 0[/COLOR]
```


The above UUID in red does not exist anymore and you certainly can't mount it to the pseudo file /dev/sda3

```
sudo parted -l
[sudo] password for czanat: 
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 106MB 105MB primary ntfs
[COLOR="#008000"][B]2 106MB 41,1GB 41,0GB primary ntfs boot
3 41,1GB 148GB 107GB primary ntfs[/B][/COLOR]
4 148GB 320GB 172GB extended
5 148GB 170GB 22,8GB logical ext4
6 170GB 196GB 26,0GB logical ext4
7 196GB 217GB 20,9GB logical ext4
8 217GB 240GB 23,0GB logical ext4
9 240GB 262GB 21,6GB logical ext4
12 262GB 287GB 25,4GB logical ext4
10 287GB 317GB 30,0GB logical ext4
11 317GB 320GB 2718MB logical linux-swap(v1)
```

The data shows the same two ntfs partitions.  No matter what you call it you only have 2 partitions that are ntfs (shown in green)

Learn to use the [code] blocks for this kind of data.  I don't want to reformat it.  You should do that task.

---

### Post by Chanath on 2014-07-28
I have 3 ntfs partitions. One is called "System Reserved,(sda1)" the other is the Windows 8 (sda2) and the third is Data (sda3). This was like this for years. The rest is used for Linux. 
All other Linux distros (some are derived of 14.04 base) see sda3, while vanilla Ubuntu 14.04 doesn't.

Here is what one of the other 14.04 based linux distro sees;

   > cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=ab381cfa-3db3-4fb5-bab4-fd76bd735f50 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=636c9885-b16f-4b8d-bf1f-e77339632b60 none            swap    sw              0       0

>  sudo parted -l
[sudo] password for czanat: 
Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs
 2      106MB   41,1GB  41,0GB  primary   ntfs            boot
 3      41,1GB  148GB   107GB   primary   ntfs
 4      148GB   320GB   172GB   extended
 5      148GB   170GB   22,8GB  logical   ext4
 6      170GB   196GB   26,0GB  logical   ext4
 7      196GB   217GB   20,9GB  logical   ext4
 8      217GB   240GB   23,0GB  logical   ext4
 9      240GB   262GB   21,6GB  logical   ext4
12      262GB   287GB   25,4GB  logical   ext4
10      287GB   317GB   30,0GB  logical   ext4
11      317GB   320GB   2718MB  logical   linux-swap(v1)

> ~ $ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="085E76845E766A78" TYPE="ntfs" 
/dev/sda2: UUID="2A6CFF786CFF3D5F" TYPE="ntfs" 
/dev/sda3: LABEL="Data" UUID="4701A4C61D83C5C4" TYPE="ntfs" 
/dev/sda5: UUID="eb85a743-c857-486d-87e1-779c42f6b774" TYPE="ext4" 
/dev/sda6: UUID="ab381cfa-3db3-4fb5-bab4-fd76bd735f50" TYPE="ext4" 
/dev/sda7: UUID="63e64b4a-1a5b-42bd-b04d-ff8fe6c40995" TYPE="ext4" 
/dev/sda8: UUID="9d895c9e-a5c6-448b-bc96-904c6d18751e" TYPE="ext4" 
/dev/sda9: UUID="9224f728-8681-4690-aa3f-e00acba7b55b" TYPE="ext4" 
/dev/sda10: UUID="5d0c66eb-d6ff-4e70-a81d-3681071023eb" TYPE="ext4" 
/dev/sda11: UUID="636c9885-b16f-4b8d-bf1f-e77339632b60" TYPE="swap" 
/dev/sda12: UUID="afcc1c95-c95f-4d15-b1a2-bdc437310066" TYPE="ext4"

---

### Post by Chanath on 2014-07-28
Anyway, I found the solution. I simply deleted 
UUID=4701A4C61D83C5C4 /dev/sda3  ntfs-3g  defaults,windows_names,locale=en_US.utf8 ro  0 0 			 		
from fstab and rebooted Ubuntu 14.04.

Only, this shouldn't happen after a dist-upgrade.

---

### Post by bab1 on 2014-07-28
> **Chanath said:**
> Anyway, I found the solution. I simply deleted 
UUID=4701A4C61D83C5C4 /dev/sda3  ntfs-3g  defaults,windows_names,locale=en_US.utf8 ro  0 0 			 		
from fstab and rebooted Ubuntu 14.04.

Only, this shouldn't happen after a dist-upgrade.

But it did and you finally fixed it.  :D

---

