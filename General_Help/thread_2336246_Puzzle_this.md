---
title: "Puzzle this"
date: 2016-09-06
forum: General Help
---

### Post by cardinal548 on 2016-09-06
I have for sometime been trying to get Linux on my laptop using a usb flash drive. I've been using several startup disk creators to use as the usb boot drive. I believe I may have inadvertainly at some point got the usb flash drive and my external usb data drive mixed up and as a result have lost access to my external usb data drive. It will not mount and the error msg is:
```

 Error mounting /dev/sdc1 at /media/jucick/Ubuntu 16.04.1 LTS amd64: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500" "/dev/sdc1" "/media/jucick/Ubuntu 16.04.1 LTS amd64"' exited with non-zero exit status 32: mount: /dev/sdc1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
```
The label"Ubuntu 16.04.1 LTS amd64" is not correct and the mount point "iso9660" is well what can I say?
If this is indeed correct how might I correct it or more importantly save the data?

---

### Post by HermanAB on 2016-09-06
Howdy,

You may be able to get some files back using ddrescue.

Note that there is a lot of wrong information about Ubuntu install disks on teh intertubes.  Since many years, the Ubuntu ISO files are dual mode, same as everybody else - they eventually caught up.  So all you need to do to make an install USB flash disk is to write the ISO file to it byte for byte with rawrite on Windows, or dd on Linux or Mac (or even with cat).

---

### Post by mook765 on 2016-09-06
Hello cardinal548, I followed your previous threads and it seems you didn't get useful help yet.
I think that you burned the Ubuntu-installation-iso to your data-stick. That means that some of your data are overwritten. But some data might be left. The problem is how to access them.
Ubuntu tries to mount the stick as a CD because you burned the iso-image to the stick, and even this mount-attempt seems to fail now.
I see only one chance to recover data from your stick. Install testdisk.```
sudo apt-get install testdisk
```
Then run ```
sudo testdisk /list
```
to see a list of connected devices. Would be good to have only the problematic stick connected to your machine to avoid confusion.
Your hard-drives will be listed as well.
Figure out which of the devices is your stick.
Then run```
sudo testdisk
```
You have to use the arrow-keys to scroll through the menus then, everything in terminal, it is a bit self-explaining, but not always easy to understand. You have to fiddle around.
I just took my stick with the Ubuntu-iso, this stick is mounted as CD as well on my machine and let teskdisk analyze the stick.
It was really checking the whole stick, needed about half an hour for 8 GB. and that was not a deeper scan yet, so be prepared to be patient.
If you can't use Ubuntu in any way, testdisk is available for windows too.
Here you can find  a step-by-step-guide and more information about testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Hope you can save some data from your stick this way, good luck...

---

### Post by cardinal548 on 2016-09-06
Mook765 I installed testdisk and am to where I need to select the partition table type, I am in doubt as to which one to select. Btw the flash stick is what I was using to boot my laptop, the drive I can not mount is a 3tb external usb drive.

---

### Post by mook765 on 2016-09-06
Selcect <none> first, we will see what is going...
In next menu select <Analyze>...
then press just enter...
Now it will take some time, you may go for coffee...

---

### Post by cardinal548 on 2016-09-06
These are the results, what next?
```
Disk /dev/sdc - 3000 GB / 2794 GiB - CHS 45600 255 63
     Partition               Start        End    Size in sectors
>P ext4                     0   1  1 45600  41 63  732566583 [ARK]











Structure: Ok.


Keys T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large_file Sparse_SB Backup_SB, 3000 GB / 2794 GiB

```

---

### Post by mook765 on 2016-09-06
hit the "P"-key
Was this gpt or mbr disk?

---

### Post by cardinal548 on 2016-09-06
eek don't like the looks of that, all it was looking so good
```
   P ext4                     0   1  1 45600  41 63  732566583 [ARK]
Directory /

No file found, filesystem may be damaged.














Use Right to change directory, h to hide deleted files
    q to quit, : to select the current file, a to select all files
    C to copy the selected files, c to copy the current file

```

---

### Post by mook765 on 2016-09-06
That sounds bad...
You had only one partion on the drive?
was this drive gpt or mbr ?

---

### Post by cardinal548 on 2016-09-06
```
jucick@Home:~$ sudo lsblk
[sudo] password for jucick: 
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0  37.3G  0 part /
&#9500;&#9472;sda2   8:2    0   4.7G  0 part [SWAP]
&#9492;&#9472;sda3   8:3    0 181.7G  0 part /home
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part 
sdc      8:32   0   2.7T  0 disk 
&#9500;&#9472;sdc1   8:33   0  11.3G  0 part 
&#9492;&#9472;sdc2   8:34   0  18.5M  0 part 
jucick@Home:~$ sudo gdisk -l
GPT fdisk (gdisk) version 1.0.1

Problem opening -l for reading! Error is 2.
The specified file does not exist!
jucick@Home:~$ sudo gdisk
GPT fdisk (gdisk) version 1.0.1

Type device filename, or press <Enter> to exit: /dev/sdc
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: present
  GPT: not present


*******************************************************************
This disk appears to contain an Apple-format (APM) partition table!
It will be destroyed if you continue!
*******************************************************************


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************

Warning! Main partition table overlaps the first partition by 6 blocks!
You will need to delete this partition or resize it in another utility.

Command (? for help): 

```

---

### Post by mook765 on 2016-09-06
The drive should be gpt anyway, if something will be left on the drive i am unable to answer...
for the moment i think, run testdisk again, this time choose <EFI/GPT> partition-type, and scan again...

---

### Post by cardinal548 on 2016-09-06
I'm trying get detailed info on a partition, but not got the command correct do you know it?
```
Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): i
Partition number (1-2): 

```

---

### Post by mook765 on 2016-09-06
When you burned the iso to the drive, you overwrote the MBR, the partitiontable and for sure a part of the first partition on the disk. so your root-partition is gone . did you have a separate home-partition?
wait a moment. i will try to find out, how to restore the partition-table from backup...
If you are still on that screen choose option "v".

---

### Post by cardinal548 on 2016-09-06
```
Disk /dev/sdc - 3000 GB / 2794 GiB - CHS 45600 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Bad GPT partition, invalid signature.
Trying alternate GPT
Bad GPT partition, invalid signature.


```
```
Disk /dev/sdc - 3000 GB / 2794 GiB - CHS 45600 255 63
     Partition               Start        End    Size in sectors
>P MS Data                       63  732566645  732566583 [ARK]











Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
                P=Primary  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large_file Sparse_SB Backup_SB, 3000 GB / 2794 GiB

```

---

### Post by mook765 on 2016-09-06
"L" loads backup
Here some background-information:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by cardinal548 on 2016-09-06
Tried and no backup found, not good. And I believe that brings us to the end of this adventure. 
Did deeper partition search, did not look promising so stopped short
Can the drive be formatted and still usable?

---

### Post by mook765 on 2016-09-06
I really think so, we need to create protective mbr and create new partition-table.
Read a bit in the link i give in one of my last posts, it's pretty interesting.
Many ways to go, maybe you can use gparted to give the drive a new life.
Data seems to be gone, or you would need a specialist for forensic to get them back.
For the future just be careful, do nice partitioning. keep system and private data separate on different partitions.
You don't need huge partitions for the operating system. I give my system partition about 40 GB, this is generous, even if i don't have a separate home-partition. My private data are on different partitions and i use links to work with them in my system. This way, in my home-folder are only the configuration-files and, off course, the links to my private data folders...
That was a bad accident burning the iso to the drive, but this can happen...
I need rest now, i will be back and see what's going...
See you later...

---

### Post by cardinal548 on 2016-09-06
Using the Disks app shows that there is a total of 31mb on both partitions, I can assume by this that there is nothing of value left to save.

---

### Post by cardinal548 on 2016-09-06
Thanks Mook765 for all your help I appreciate it. I'll read up at that link looks very interesting so far. Thanks again.

---

### Post by sudodus on 2016-09-06
If you have not yet overwritten the drive, you could try to recover some information without a file system. Testdisk's sister program ***PhotoRec*** from [http://www.cgsecurity.org/](http://www.cgsecurity.org/) can do that.

At least PhotoRec can find some of the data. The file content, that is not yet overwritten can be identified via 'signiatures' in the data itsulf. It will be hard work, because it will be dumped without the original file names, and there will be no directory structure, but if the data is valuable, it can still be worth the effort.

-o-

Do not let the name PhotoRec confuse you ;-) It was originally created to recover photos from memory cards with corrupted file systems. Now it can identify most of the used file format for documents, multimedia, etc, so I suggest that you give it a chance.

---

