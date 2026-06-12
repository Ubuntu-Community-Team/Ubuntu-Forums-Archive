---
title: "External 2 TB Hard drive suddenly read only"
date: 2014-12-09
forum: General Help
---

### Post by polardude1983 on 2014-12-09
I have an external 2 TB Hard drive that suddenly became read only. At least that's what it says when I try to rename a file in the terminal command.

I have folders that show that there are files and I can see them. But one folder I cannot.

I have a folder called Test. It is in /media/2TB/Test

When I open the folder it shows 0 items are in that folder, but I know there are over 200 files in that folder.

but if i go to terminal and go to /media/2TB/Test and do a dir function it spits out results for over 200 files.

any help is appreciated

This is what I get from the Sudo fdisk -l command

```
sudo fdisk -l
[sudo] password for christoph: 


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00017adf


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   563826687   281912320   83  Linux
/dev/sda2       612855806   625141759     6142977    5  Extended
/dev/sda5       612855808   625141759     6142976   82  Linux swap / Solaris


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea90e


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   119676927    59837440   83  Linux
/dev/sdb2       522112500   976768064   227327782+  83  Linux
/dev/sdb3       119676928   522110975   201217024   83  Linux


Partition table entries are not in disk order


WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdg: 2000.4 GB, 2000398933504 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x089c2f1e


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1  3907029166  1953514583   ee  GPT
christoph@christoph-System-Product-Name:~$ 
```




I can't even create directories as root either on this hard drive. and Gparted hangs on scanning forever.

---

### Post by Impavidus on 2014-12-10
In case of an I/O error the partition is automatically remounted read-only, to prevent further file system damage. So this could be a hardware error.

---

### Post by oldfred on 2014-12-10
Did you try fsck? If sudden shutdown or powerfailure that can cause corruption that fsck may be able to fix.
Run on all ext family of partitions on drive.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by leunam12 on 2014-12-10
Did you plug it in a Windows computer? Maybe it was not ejected properly.

---

### Post by polardude1983 on 2014-12-10
I do need to run a fsck on the drive. But no it was not plugged into a windows computer.

---

### Post by polardude1983 on 2014-12-11
So this is what I got from the e2fsck for the hard drive

```
2TB: ***** FILE SYSTEM WAS MODIFIED *****

    4472 inodes used (0.00%)
     140 non-contiguous files (3.1%)
       9 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 13/13/13
         Extent depth histogram: 2948/1513/1
431571980 blocks used (88.37%)
       0 bad blocks
      43 large files


    3837 regular files
     624 directories
       0 character device files
       1 block device file
       0 fifos
       0 links
       1 symbolic link (1 fast symbolic link)
       0 sockets
--------
    4419 files
christoph@christoph-System-Product-Name:~$ 
```

So no when I have the Test folder selected it says contains 419 items. But when I try to open the folder it just gets stuck at loading forever

---

### Post by oldfred on 2014-12-11
Your fdisk does not show the partition on a gpt drive, it just shows the protective MBR.

What does this say:

If you do not have gdisk
sudo apt-get install gdisk

sudo gdisk /dev/sdc -l

---

