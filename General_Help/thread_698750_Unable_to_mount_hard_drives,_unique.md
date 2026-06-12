---
title: "Unable to mount hard drives, unique"
date: 2008-02-16
forum: General Help
---

### Post by serendipitousus on 2008-02-16
I have several partitions on two disks, and I can't mount them. Help would be most appreciated. 

Here's what I think happened. I belive I installed windows in some empty disk space, and then deleted it. Now I can't get to any of my partitions. I don't remember how many were where, but I'm pretty sure they were all ext3 except for one NTFS. I tried to use a live disk, and when I try to mount one of the drives

```

ubuntu@ubuntu:/$ sudo mount /dev/hda -t ext3 /mnt/test
mount: wrong fs type, bad option, bad superblock on /dev/hda, 
             missing codepage or other error
             In some cases useful info is found in syslog - try
             dmesg | tail   or so

```

doing so returns
```

ubuntu@ubuntu:/$ dmesg | tail
[591859.672779] cramfs: wrong magic
[591859.684151] unable to indentify CD-ROM format
[591859.687855] SQUASHFS error: Can't find a SQUASHFS superblock on hda
[591992.875956] VFS: Can't find ext3 filesystem on dev hda
[592025.901704] NTFS driver 2.1.28 [Flags: R/O MODULE]
[592025.903058] NTFS-fs warning (device hda): is_boot_sector_ntfs(): Invalid boot sector checksum. 
[592025.903065] NTFS-fs error (device hda): read_ntfs_boot_sector(): Primary boot sector is invalid. 
[592025.903069] NTFS-fs error (device hda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[592025.903072] NTFS-fs error (device hda): ntfs_fill_super(): Not an NTFS volume.
[592084.647696] VFS: Can't find ext3 filesystem on dev hda

``` 


```

ubuntu@ubuntu:/$ ls -la /dev | grep hd
lrwxrwxrwx 1 root root              3 2002-05-30 21:50 cdrom -> hdc
lrwxrwxrwx 1 root root              3 2002-05-30 21:50 cdrw -> hdc
lrwxrwxrwx 1 root root              3 2002-05-30 21:50 dvd -> hdc
lrwxrwxrwx 1 root root              3 2002-05-30 21:50 dvdrw -> hdc 
brw-rw----   1 root disk        3,   0 2002-05-30 21:48 hda
brw-rw----   1 root disk        3,  64 2002-05-30 21:48 hdb
brw-rw----   1 root disk        3,  65 2002-05-30 21:48 hdb1
brw-rw----   1 root cdrom  22,    0 2002-05-30 21:48 hdc
brw-rw----   1 root cdrom  22,   64 2002-05-30 21:48 hdd

```

I was able to get the ntfs drive to mount, its entry in /etc/mtab is 

```

/dev/hdb1 /mnt/disk1 ntfs rw 0 0

```

however, I am unable to cd to it, ls on it, or chmod it

```

ubuntu@ubuntu:/$ ls -la /mnt | grep disk1
dr-x------     1 root root 24576 2002-05-25 03:29 disk1

```

I'm fairly sure that these are valid ext3 partitioned disks. Again, if someone could help me get at them,  or give me a hint as to what's going wrong, huge kudos. I'm on Feisty if it matters, and if there's any other info I can provide, lemme know.

Thank you!

---

### Post by pointone on 2008-02-16
Post the output of the following commands:

```
sudo fdisk -l /dev/hda
sudo fdisk -l /dev/hdb
```

---

### Post by serendipitousus on 2008-02-16
Since this post I ran parted, and ran rescue on hda, and I found another NTFS partition. 

 Here they are 

```

ubuntu@ubuntu:/dev$ sudo fdisk -l /dev/hda

Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

       Device Boot             Start           End             Blocks        Id         System
/dev/hda1                            1          2550      20482843         7         HPFS/NTFS

```

```

ubuntu@ubuntu:/dev$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

      Device Boot              Start           End             Blocks         Id         System
/dev/hdb1    *                       1       26771    215038026          7         HPFS/NTFS

```

---

### Post by serendipitousus on 2008-04-08
I got another boot disk, this one contains testdisk. I ran it under sudo, on both of my devices, and it returned the following information 

When I first select HDA, it displays the following information
```

Disk /dev/hda - 300 GB / 279 GiB - CHS 36483 255 63

Current partition structure

       Partition    Start     End      Size in Sector

Error: size boot_sector 40965687 > partition 40965686

Invalid NTFS Boot 

1 P HPFS - NTFS   0   1   1   2549     254     62     40965686

1 P HPFS - NTFS   0   1   1   2549     254     62     40965686

No partition is bootable

```

When I tell testdisk to search for partitions on HDA, it comes up with the following
```

Disk /dev/hda - 300 GB / 279 GiB - CHS 36483 255 63

    Partition        Start               End         Size in Sectors
D HPFS - NTFS           0  1   1         2549      254    63      40965687
D Linux          2550   0   1         3999      254    63      23294250    [/]
D Linux Swap      4000   0   1         4499      254    63      8032500
D Linux           4500   0   1         7186      254    63      43166655
D FAT32  LBA    26139   0   1       31135      254    63      80276805    [No Name]
D Linux         31136   2   1       35899      254    63      76533534   [/]
D Linux Swap    35900   1   1       36105      254    63       3309377

```

Here's the info for HDB. It doesn't come up with anything different when I tell it to search
```

1 *  HPFS-NTFS      0    1    1      26770     256     63      430076052

```

I'm not rightly sure what this means, or how I can get my data off of these devices. Any help would be appreciated.

---

### Post by serendipitousus on 2008-04-19
From what I've been able to determine, my partition table is corrupted. I'm not sure what I did to corrupt it; it must have happened when I was loading windows.

I got a new HDD and loaded linux on it, that way I can save information, and hopefully copy over recovered partitions to my new drive. I set one of my non-functioning drives as a slave, and I'm running testdisk diagnostics on it. From what I can tell on the testdisk wiki 

[http://www.cgsecurity.org/wiki/TestDisk]("http://cgsecurity.org/wiki/TestDisk")

this is what I need to be doing. (Though exactly how this gets me my data back is still hazy)

I just performed a deep search, which I believe also searches backup superblocks and backup boot sectors, and it gave me this picture of the data laid out on the disk.

```

Disk /dev/hda - 300 GB / 279 GiB - CHS 36483 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  2549 254 63   40965687
D Linux                 2550   0  1  3999 254 63   23294250 [/]
D FAT32 LBA             2550   1  1  3999 254 63   23294187 [NEW VOLUME]
D Linux                 3039   0  1 27353 254 63  390620475 [/home]
D Linux                 3282   0  1 27353 254 63  386716680 [/home]
D Linux Swap            4000   0  1  4499 254 63    8032500
D Linux                 4500   0  1  7186 254 63   43166655
D FAT32 LBA            26139   0  1 31135 254 63   80276805 [NO NAME]
D FAT32 LBA            27354   0  1 36482 254 63  146657385 [NO NAME]
D Linux                31136   2  1 35899 254 63   76533534 [/]
D Linux Swap           35900   1  1 36105 254 63    3309327
D Linux Swap           36105   1  1 36482 254 63    6072507

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 20 GB / 19 GiB

```

I don't know what to do with this information. If this makes clear to someone how my partition table is corrupted, and what to do about it, help would be appreciated.

---

### Post by bodhi.zazen on 2008-04-19
Lets back up a little.

The problem is you need to specify a partition. Your command :

> sudo mount **/dev/[color=red]hda[/color]** -t ext3 /mnt/test

is off. hda = the entire hard drive.

You need /dev/hda1

First, list your partitions with :

```
sudo fdisk -l
```

Then make a mount point and mount :

```
sudo mkdir /media/hda1
sudo mount **/dev/[color=blue]hda1[/color]** /media/hda1
```

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by serendipitousus on 2008-04-20
You are quite right, I mistyped that. 
[SIZE="1"]
Most of the above commands, except for the last post, were entered in a live environment, and I didn't have access to a network, so I had to type all of that input by hand. 
[/SIZE]
However, I still believe that my partition table is corrupted. 

```
jhemann@Protagoras:/dev$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa42aa42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS

```

That is the only partition listed. At least a couple of the others that testdisk picked up are valid - it will list the files.

---

### Post by serendipitousus on 2008-04-20
I edited the partitions list using tesdisk, and changed some of the partitions from deleted to primary, and I am now able to mount them. 

I can get some of my data in this fashion.

Also, interestingly (but probably unrelated) my IDE hard drive (one of the problematic ones) is now being recognised as sdb. My new primary drive is a new SATA device, and I assume its somehow related to that.

---

### Post by serendipitousus on 2008-05-17
So when I was fixing this, I found this website to be really helpful. It might help someone else too if you are coming across this problem.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

It has examples of testdisk usage, and walks you through the application step-by-step. If you aren't a forensics expert (and if you're here, you probably aren't) then it might be enough to get you through.

---

### Post by serendipitousus on 2008-05-17
It's also good practice to save an image of that drive before you mess around with it. If you are in this state, it's obviously possible for you to make errors.

ddrescue works well, use dd if you have to. 

this howto might be enough to help you get started with it. 

[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

---

### Post by greco8523 on 2008-06-20
TestDisk only detects and writes the information for the partition you will need to run other utilities to correct the corruption such as  e2retrieve. 

This link for some other utilities: 
[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

---

