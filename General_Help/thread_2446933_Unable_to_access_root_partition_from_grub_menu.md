---
title: "Unable to access root partition from grub menu"
date: 2020-07-09
forum: General Help
---

### Post by arolihas on 2020-07-09
Hello guys, I am in a lot of trouble so any help would be appreciated.

I have a dual boot on my laptop with Windows and Ubuntu and I wanted to resize my partitions. I shrunk my Windows partition using gparted and grew the active ubuntu partition to fill the unallocated space using the first answer here: [https://askubuntu.com/questions/24027/how-can-i-resize-an-ext-root-partition-at-runtime](https://askubuntu.com/questions/24027/how-can-i-resize-an-ext-root-partition-at-runtime)

This seemed to have worked, but when I rebooted the computer to apply the new partition tables, I get the grub menu at Ubuntu boot. I can boot into Windows just fine. I've seen a lot of posts about finding the /boot/grub/ folder and loading the image and kernels from there to boot, but I cannot find this folder in my root partition. My main partition, /dev/sda5 or (hd0,gpt5) is now an unknown filesystem. 

I tried to use boot-repair from USB and the results for that are here: [https://paste.ubuntu.com/p/Tx7SgFJFh5/](https://paste.ubuntu.com/p/Tx7SgFJFh5/). It said successful boot repair but when I reboot I still get the grub menu and I cannot find /boot/grub directory anywhere. What do I do?

---

### Post by oldfred on 2020-07-09
First always use Windows tools to resize Windows & reboot into Windows to make sure it runs chkdsk. While gparted can often resize NTFS partitions, when issues everyone blames Linux when often a Windows issues. 
General rule is Windows tools for Windows & Linux tools for Linux.

You first need to change sda5 to ext4, assuming it was ext4  & your / partition. But do not want to format it, just change partition table entry. Then you probably need full fsck. Many tools that create partitions, both create it & format it, which you do not want.

Do you have good backups, particularly /home, & list of installed apps and maybe /etc if you changed any system settings? 

backup partition table before any changes, so you can get back to current if changes not correct, save to another device. This is just a text file of partitions, so you can easier restore partition table.
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

What does gdisk show as it loads & compare gpt partition table with backup gpt partition table.
sudo gdisk -l /dev/sda
[https://www.rodsbooks.com/gdisk/repairing.html](https://www.rodsbooks.com/gdisk/repairing.html)

What does testdisk show? It typically finds all old partitions show may show multiple versions of each partition, since resized.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]https://help.ubuntu.com/community/DataRecovery#Lost_Partition


[/URL]#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

### Post by arolihas on 2020-07-09
I don't have any good backups so I can't run those commands :(. I'm a little confused, sorry, should I boot ubuntu from a usb and try those commands?

I'm running testdisk in my Windows partition right now. The partition was labeled as Linux filesystem data, and I couldn't read any of the filesystems inside. I tried to change the type to linux /home and /src with ext4 but it still couldn't read the filesystem. I'm performing quick search for partitions and it's taking a long time, stuck at 72%.

---

### Post by oldfred on 2020-07-09
Best to run Linux repairs from Linux.
Windows tools have been known to damage Linux partitions as they just do not see them correctly. So not know about testdisk in Windows.

Use your Ubuntu live installer.
You want to backup partition table before anything else.
If testdisk deeper search shows any files, then copy those to your backup drive just in case later you can not get them.

Also run gdisk as it sees gpt the best of most tools.

---

### Post by arolihas on 2020-07-24
Hello again,

Thank you for your advice so far. I have gdisk running on my boot repair disk since it is based off of Ubuntu (Lubuntu)

For /dev/sda, here are the following outputs for basic commands:
p
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Model: ST500LM021-1KJ15
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): DDA3B9D5-792B-484E-B540-BC37F1FC154D
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2029 sectors (1014.5 KiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          534527   260.0 MiB   EF00  EFI system partition
   2          534528          567295   16.0 MiB    0C01  Microsoft reserved ...
   3          567296       350593023   166.9 GiB   0700  Basic data partition
   4       974725120       976773119   1000.0 MiB  2700  Basic data partition
   5       350593024       958162943   289.7 GiB   8300  
   6       958162944       974725119   7.9 GiB     8200  


i 5 (info on partition 5, my Ubuntu partition I cannot access)
Partition number (1-6): 5Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 3F0D5A3F-51B1-7D4B-9675-58DF04EE44A7
First sector: 350593024 (at 167.2 GiB)
Last sector: 958162943 (at 456.9 GiB)
Partition size: 607569920 sectors (289.7 GiB)
Attribute flags: 0000000000000000
Partition name: ''


v
No problems found. 2029 free sectors (1014.5 KiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

---

### Post by oldfred on 2020-07-24
Then from live installer have you run fsck?
man e2fsck

sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, so run both commands
sudo e2fsck -C0 -p -f -v /dev/sda5
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

### Post by arolihas on 2020-07-24
This is my output for sudo parted -l

Model: ATA ST500LM021-1KJ15 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  274MB  273MB   fat32           EFI system partition          boot, hidden, esp
 2      274MB   290MB  16.8MB                  Microsoft reserved partition  msftres
 3      290MB   180GB  179GB   ntfs            Basic data partition          msftdata
 5      180GB   491GB  311GB
 6      491GB   499GB  8480MB  linux-swap(v1)
 4      499GB   500GB  1049MB  ntfs            Basic data partition          hidden, diag




Model: General UDisk (scsi)
Disk /dev/sdb: 1006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1006MB  1005MB  primary  fat32        boot, lba




Model: Unknown (unknown)
Disk /dev/zram3: 1029MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1029MB  1029MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram1: 1029MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1029MB  1029MB  linux-swap(v1)




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: General UDisk (scsi)                                               
Disk /dev/sr0: 233kB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 


Model: Unknown (unknown)
Disk /dev/zram2: 1029MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1029MB  1029MB  linux-swap(v1)




Model: Unknown (unknown)
Disk /dev/zram0: 1029MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1029MB  1029MB  linux-swap(v1)


For the e2fsck commands should I use the partition I want to recover? You say replace /dev/sda5 with my partition but I don't know which partition you are referring to and I don't want to mess anything up even further

---

### Post by oldfred on 2020-07-24
I changed my generic post to your specific /dev/sda5 as that is your only Linux partition.
You can only run fsck or e2fsck on unmounted ext2, ext3 or ext4 formatted partitions.

---

### Post by arolihas on 2020-07-25
My output for both of those commands:

lubuntu@lubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Bad magic number in super-block while trying to open /dev/sda5
/dev/sda5: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


lubuntu@lubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda5


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Should I give those a try?

---

### Post by oldfred on 2020-07-25
Next alternative to try to recover is thealternate superblock.

If that does not work, you should make an image of partition on another drive and run photorec or other scan tools.
Or just reinstall & restore from backup.

---

### Post by arolihas on 2020-07-25
Neither alternate superblock worked :(

How can I make an image of a corrupted unrecognized partition?

---

### Post by oldfred on 2020-07-25
See section on imaging damaged drive or partition. 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

gddrescue better than ddrescue
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

---

### Post by arolihas on 2020-07-31
So I downloaded gddrescue and got my hands on an old 500GB hard drive. Below is the logfile  

# Mapfile. Created by GNU ddrescue version 1.22
# Command line: ddrescue --force /dev/sda5 /dev/sdb1 /home/logfile
# Start time:   2020-07-30 15:31:27
# Current time: 2020-07-30 16:20:55
# Finished
# current_pos  current_status  current_pass
0x486D8F0000     +               1
#      pos        size  status
0x00000000  0x486D900000  +

I've looked at different directions because I'm a little confused and I'm scared of screwing something up again to be honest. It seemed like ddrescue was successful. But when I open gparted I don't see any space being taken up by the partition on my /dev/sdb1 drive. I assumed approx 300GB would be taken up in there but it only shows an unkown partition of size 465GB. 

I also downloaded sleuthkit per the data recovery website but I don't know where to go from here. When I ran

```
sudo mmls /dev/sdb1
```

I get "Cannot determine partition type"

What should I do next?

---

### Post by oldfred on 2020-07-31
Can you run photorec on your sdb1 partition or sdb drive?
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

It needs another drive to copy data to as you cannot copy it to same drive you are scanning?

---

### Post by arolihas on 2020-08-01
So I'm booting from lubuntu on a flash drive. I just imaged /dev/sda5 onto a separate drive which is /dev/sdb1. Are you saying I need a third hard drive then for photorec? Couldn't I run photorec on /dev/sda5 and copy it over to /dev/sdb1?

---

### Post by oldfred on 2020-08-01
You can, but the suggestion is always to have an image backup, just in case.

Photorec will find even deleted files & parts of very old files that may have been partially overwritten. It only gives you extension, not full filename.
I had to run it overnight and then took weeks part time to investigate each file and it turned out I had saved some many times so had lots of duplicates, but no date to know which was newest. Lots of compares to backkup which was a bit old.
Learned to do better backups.

---

