---
title: "Can't recover lost data"
date: 2014-07-25
forum: General Help
---

### Post by andrew-nykyforuk on 2014-07-25
[COLOR=#000000][FONT=tahoma]Let me start from the beginning.[/FONT][/COLOR]

[COLOR=#000000][FONT=tahoma]I have desire try to use ubuntu 14.04.1 LTS. Before installing I had two NTFS partition, in one of them was located important data. Mistakenly I formatted HDD. Realizing that I was made a mistake, I recover lost data and after this I'm again tried to install ubuntu...Everything is going good, but when I divide HDD into two partitions(ext4,fat32) - I was compelled select "mounting point" or something like this...I made it. Ext4 mounting point - /root, fat32 mounting point - /windows. Honestly, I did not realize what I doing...Installation was successful.[/FONT][/COLOR]

[COLOR=#000000][FONT=tahoma]Then, I needed to transfer lost data to a disk. I didn't see any my partition, just like "Computer" device. There was a folder "/windows". I thought that this is probably my part where I can save my lost data. But after the transfer data in this directory, ubuntu no longer start up. I reboted, over and over...Nothing has changed. I tried to boot from another computer, but in directory /windows - nothing was attended(Empty folder).

Please help me to understand, what's going on?! What can i do?

Extended partition it's probably my fat32 part...But why he's extended...can't understand - nothing...pls help.
[/FONT][/COLOR][IMG]http://cs620731.vk.me/v620731391/1400d/APkp_i8QnYw.jpg[/IMG]

---

### Post by oldfred on 2014-07-25
You have two hard drives.
Post this:
sudo parted -l

You used to only be able to create Linux partitions during install. But I always created partitions in Advance with gparted and then use Something to choose / (root).

Also best not to use FAT32. Max file size is 4GB and it does not have a journal so data recovery is harder or impossible. If you need compatibility with Windows better to use NTFS.

---

### Post by andrew-nykyforuk on 2014-07-25
Yes, I have two hard drives. But the problem with only one of them(320GB). Another I use in order to recover a data. 

Just don't understand where is all data was stored and why ubuntu no longer boot.

[COLOR=#808080]Model: ATA ST1000LM024 HN-M (scsi)[/COLOR]
[COLOR=#808080]Disk /dev/sda: 1000GB[/COLOR]
[COLOR=#808080]Sector size (logical/physical): 512B/512B[/COLOR]
[COLOR=#808080]Partition Table: msdos[/COLOR]
[COLOR=#808080]
[/COLOR]
[COLOR=#808080]Number  Start   End     Size    Type      File system     Flags[/COLOR]
[COLOR=#808080] 1      1049kB  992GB   992GB   primary   ext4            boot[/COLOR]
[COLOR=#808080] 2      992GB   1000GB  8438MB  extended[/COLOR]
[COLOR=#808080] 5      992GB   1000GB  8438MB  logical   linux-swap(v1)[/COLOR]
[COLOR=#808080]
[/COLOR]
[COLOR=#808080]
[/COLOR]
[COLOR=#808080]Model: ATA WDC WD3200BEVT-7 (scsi)[/COLOR]
[COLOR=#808080]Disk /dev/sdb: 320GB[/COLOR]
[COLOR=#808080]Sector size (logical/physical): 512B/512B[/COLOR]
[COLOR=#808080]Partition Table: msdos[/COLOR]
[COLOR=#808080]
[/COLOR]
[COLOR=#808080]Number  Start   End     Size    Type      File system     Flags[/COLOR]
[COLOR=#808080] 1      1049kB  61,5GB  61,5GB  primary   ext4            boot[/COLOR]
[COLOR=#808080] 2      61,5GB  320GB   259GB   extended[/COLOR]
[COLOR=#808080] 5      61,5GB  318GB   256GB   logical[/COLOR]
[COLOR=#808080] 6      318GB   320GB   2047MB  logical   linux-swap(v1)[/COLOR]

---

### Post by oldfred on 2014-07-25
Neither drive is showing any NTFS partitions.
Did you use the auto reinstall options? Those overwrite entire drive.
       
Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

With two drives you need to always use Something Else. Often better to use gparted to partition in advance.

If you have data you did not backup, you may be able to recover some of it, but it will be a long slow process. And you must STOP using system and only use live installer.

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)
      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

      
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

