---
title: "Erase a hard drive to RAW data in terminal"
date: 2013-01-31
forum: General Help
---

### Post by magace on 2013-01-31
Hello I cant seem to figure out how to quick erase a drive to RAW space. Can anyone please help me.  It needs to be done in terminal.  I figured out how to use mkfs to create partitions but cant find anything on quick erasing the whole drive.

For now I am using palimpsest to erase the partitions however there has to be a faster way in Terminal.  All the clicking with the new interface is a pain!

THANKS!!

---

### Post by oldfred on 2013-01-31
RAW is a partition that is NTFS but not yet formatted. Or partition table says NTFS but partition boot sector has not been properly configured for NTFS.

Do you really want to delete all partitions and totally redo it?  I would not use dd unless I have really good backups. 

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

    
This totally erases boot loader and partition table, not not actual data on drive.
       Erase - Make double sure you have correct drive 
       
 dd if=/dev/zero of=/dev/sda bs=512 count=1


I prefer to use gparted, but you have to run that from liveCD and swap off if running on the same drive as your install.

---

### Post by magace on 2013-01-31
> **oldfred said:**
> RAW is a partition that is NTFS but not yet formatted. Or partition table says NTFS but partition boot sector has not been properly configured for NTFS.

Do you really want to delete all partitions and totally redo it?  I would not use dd unless I have really good backups. 

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

    
This totally erases boot loader and partition table, not not actual data on drive.
       Erase - Make double sure you have correct drive 
       
 dd if=/dev/zero of=/dev/sda bs=512 count=1


I prefer to use gparted, but you have to run that from liveCD and swap off if running on the same drive as your install.


Thanks this works good when there is only one partition!
dd if=/dev/zero of=/dev/sdx bs=512 count=1
However when there is more than one it doesent seem to be wiping the whole drive (aka deleting all the partitions and only leaving RAW format)  Or MBR would be fine.

by the way yes im trying to just quickly delete existing partitions and leave the drive as raw I do not need to replace with zeros or anything I just want to do it as fast as It does it in disk utility when you hit format drive and select "don't partition" its practically instant.

---

### Post by kanikilu on 2013-01-31
Could you use GNU parted to do that?

```
sudo parted /dev/sdX mklabel loop
``` Where X is the target disk (a/b/c, etc.).

[https://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC16](https://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC16)

Says it doesn't technically remove the data, but makes it hard to access, and leaves no partitions. I tested this on my flash drive, and it worked fine. Had to create a new msdos partition table and new FAT32 partition on the drive afterwards to make it work again.

---

### Post by oldfred on 2013-01-31
There are only 4 partition table entries in the partition table. That is why we have the 4 primary partition limit. And writing zeros to those 4 will erase the entire partition table. 
But any logical partitions have their own partition table in each partition. But they only have one entry linking to the next logical. The extended partition in the MBR partition table is a link to the first partition table.

---

### Post by magace on 2013-01-31
update!  Sorry it was working all along.  The partitions were still showing up in disk utility however if I refresh them or take the drive out and put it back in they are actually gone.

---

### Post by dcstar on 2013-02-01
> **magace said:**
> update!  Sorry it was working all along.

Then MARK the thread.

---

