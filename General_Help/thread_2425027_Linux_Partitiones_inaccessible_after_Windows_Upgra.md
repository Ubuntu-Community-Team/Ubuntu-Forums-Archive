---
title: "Linux Partitiones inaccessible after Windows Upgrade. Partition Table messed up?"
date: 2019-08-19
forum: General Help
---

### Post by a.borque on 2019-08-19
Hello!
In my vacation my Windows 10 was upgraded from 1809 to 1903 resulting in an inaccessible Linux partitions. First I thought it was only a common problem with grub2 going into rescue-mode, but it could not be fixed there. So I started a Livesystem but the Linux partitions could not be mounted there, too. The reason for this seems to be an aditional recovery partition windows created during the upgrade (sda5).
Here are some results from what I have tried so far:

```
sudo fdisk -l

Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B44D0FE7-5E18-4122-9870-7A6CBF51044E

Device          Start        End    Sectors   Size Type
/dev/sda1        2048     923647     921600   450M Windows recovery environment
/dev/sda2      923648    1126399     202752    99M EFI System
/dev/sda3     1126400    1159167      32768    16M Microsoft reserved
/dev/sda4     1159168 1718185062 1717025895 818,8G Microsoft basic data
/dev/sda5  1718185984 1719261183    1075200   525M Windows recovery environment
/dev/sda6  1719261418 1752031231   32769814  15,6G Linux filesystem
/dev/sda7  1752031232 1817567231   65536000  31,3G Linux filesystem
/dev/sda8  1817567232 1853024255   35457024  16,9G Linux filesystem
/dev/sda9  1853024256 1886511103   33486848    16G Linux swap
/dev/sda10 1886511104 1953523711   67012608    32G Linux filesystem
```

```
sudo parted --list

Model: ATA Crucial_CT1024MX (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  473MB   472MB   ntfs         Basic data partition          hidden, diag
 2      473MB   577MB   104MB   fat32        EFI system partition          boot, esp
 3      577MB   593MB   16,8MB               Microsoft reserved partition  msftres
 4      593MB   880GB   879GB   ntfs         Basic data partition          msftdata
 5      880GB   880GB   551MB   ntfs                                       hidden, diag
 6      880GB   897GB   16,8GB
 7      897GB   931GB   33,6GB
 8      931GB   949GB   18,2GB
 9      949GB   966GB   17,1GB
10      966GB   1000GB  34,3GB
```

```

sudo mkdir /mnt/sda6
sudo mount -t ext4 /dev/sda6 /mnt/sda6
mount: /mnt/sda6: wrong fs type, bad option, bad superblock on /dev/sda6, missing codepage or helper program, or other error.
```

```
sudo fsck -t ext4 /dev/sda6
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda6

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

I have tried to guide e2fsck to the superblock backups, but they result in the same error. dump2fs refuses to work on the partitions 6-10.

Gparted sees the partitions sda6-10, but all have give the following error message

```
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda6 is missing
```

Testdisk shows the partition table as listes by fdisk, but doing a quick search no linux partition is found. Same thing for gpart.

I am out of ideas, looks like windows destroyed the partitionstable to a state that can not be recovered. 
Any suggestions aside from using an older backup?

---

### Post by TheFu on 2019-08-19
You've done what I would have and showed the commands and output I would have requested.  A **boot-info** run using the boot-repair tool might provide some extra, useful, information, perhaps.   Do not run boot-repair, just the "gather information" part.  Boot-repair hasn't been great now that there are so many possible boot permutations.

Lacking backups, [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) is all I can add.

---

### Post by oldfred on 2019-08-20
I read where Windows wanted another small recovery partition just after its main  or c: drive partition. 

Did Windows just overwrite the first 525M of your Linux partition or shrink the c: drive & add its partitions? Do you have any documentation of partition layout in detail before Windows update.

---

### Post by a.borque on 2019-08-20
Hello!   Yes, I am pretty sure the whole thing is caused by the additional recovery partition sda5 added by Windows during the feature upgrade.   Unfortunately I do not have any documentation of the layout before the update.   Indeed it was also one of my first thoughts that the new recovery partition was created by overwriting or incorrectly moving or shrinking my first linux-ext4-partion (now sda6). But all other higher partitions have the same problems (I have tried all commands mentioned above on 6-9).  And aside from the output of parted and fdisk (which look vaguely correct or at least look as I would have expected the new partition layout) there are no further signs of valid linux partitions when searching with testdisk or gpart.   So whatever happened when the new recovery partition was inserted, it did not only affect the first linux-ext4- partition after the main windows-ntfs-partition...   A.Borque

---

### Post by TheFu on 2019-08-20
Add this is another reason to avoid dual booting and use virtualization instead.  Windows runs fine inside a VM and if you are careful, you can move to new, faster, hardware without Windows knowing.

---

### Post by dragonfly41 on 2019-08-20
This is a wakeup call for me since I have a Windows 10 / Ubuntu 16.04 dual boot configuration.
I have not booted up Windows 10 for many months because of what I call "the cuckoo effect". That is Microsoft pushes other fledglings (Linux) out of the shared nest during upgrades.

I have refreshed my own notes of what is needed to mitigate against such occurrences.

First to keep records (backups) of partition table.

Install boot-repair in Ubuntu.

Have a flash drive formatted and ready to receive backup information (or alternatively save backup information in an ntfs partition which Microsoft recognises and does not throw out of the nest).

In Ubuntu launch boot-repair 

Click on Advanced Options (above the About button)

Do not click on Apply but click only on .. &#8220;Backup partition tables, boot sectors and logs&#8221;

Default location to save this information is /usr/share/boot-sav but it is safer to save into external flash drive or ntfs partition.

Unclick the Advanced Options window (do not click &#8220;Apply&#8221;) and now click on &#8220;create a Boot Info summary&#8221; and save a copy of Pastebin URL into the external flash drive or ntfs partition.

This backup information will prepare you to recover from the Windows &#8220;cuckoo effect&#8221;.

Partition tables, MBRs and logs have been saved into /media/username/SHARE/boot-save/backup_20190819_1407.zip


This old link refers (but not to latest Windows 10).

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

In my shared ntfs partition (for sharing files between Win 10 and Ubuntu) I keep my notes as a cherrytree database so that I can refer to these in both Windows and Ubuntu.  Of course cherrytree needs to be installed in both Windows and Ubuntu.  Data is saved as xml without password.


...

Now to consider the problem you now have. Since you appear to have nothing to lose by trying an experiment I would try installing R-Linux in the "upgraded" Windows 10.  Then see if R-Linux can recognise any files in your Linux partitions.


Another ploy is to bootup a Live USB (Ubuntu) and launch Gedit , Device > Attempt data rescue.

I don't understand why you have two partitions /dev/sda1 and /dev/sda5 both titled Windows recovery/
When I received my original Windows 10 there was a partition named WINRETOOLS located after the Windows OS. 
I installed Ubuntu *between* these two partitions and not after WINRETOOLS.  Again I wonder whether Windows 10 places partitions *after* WINRETOOLS.

I conclude that it is safer to keep Windows 10 and Ubuntu in separate drives.

---

