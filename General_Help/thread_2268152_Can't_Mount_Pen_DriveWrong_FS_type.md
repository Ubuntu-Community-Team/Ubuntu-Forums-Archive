---
title: "Can't Mount Pen Drive/Wrong FS type"
date: 2015-03-06
forum: General Help
---

### Post by nathanhurley on 2015-03-06
I have a pen drive which used to work, but I tried to make it bootable, and now it won't mount. I tried these instructions to no avail: [http://askubuntu.com/questions/198065/how-to-format-a-usb-drive](http://askubuntu.com/questions/198065/how-to-format-a-usb-drive)


----------When I try to click on it in file system, I get this error: 


Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so



--------Here are the results of dmesg:


nathan@nathan-PowerEdge-R200:~$ dmesg | tail
[ 1634.806156] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1634.808150]  sdc: [mac] sdc1 sdc2 sdc3
[ 1634.810887] sd 5:0:0:0: [sdc] No Caching mode page found
[ 1634.810895] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1634.810901] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[ 1635.002633] EXT4-fs (sdc3): bad geometry: block count 15687424 exceeds size of device (504 blocks)
[ 1635.089566] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[ 1637.332258] EXT4-fs (sdc3): bad geometry: block count 15687424 exceeds size of device (504 blocks)
[ 1691.216964] EXT4-fs (sdb1): ext4_check_descriptors: Checksum for group 0 failed (55309!=0)
[ 1691.216969] EXT4-fs (sdb1): group descriptors corrupted!

---

### Post by yancek on 2015-03-06
You are getting the 'wrong filesystem type' error so what is the fileystem type?  Open a terminal and type:  sudo parted -l and check the output.  The File system column should tell you and the output is similar to fdisk, the 'number' column shows the pa
rtition for each device.

---

### Post by nathanhurley on 2015-03-07
Here it is: 

Model: ATA HITACHI HTS54251 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  116GB  116GB   primary   ext4            boot
 2      116GB   120GB  4184MB  extended
 5      116GB   120GB  4184MB  logical   linux-swap(v1)

---

### Post by nathanhurley on 2015-03-07
Let me know because I will reinstall if I have to. I am using Ubuntu Studio, and used the default file system. I do not quite understand the partitioning how to do it.

---

### Post by yancek on 2015-03-07
Your initial post indicates an error when trying to mount sdb1 and your parted output refers to sda.  How many drives/partitions do you have?  You might try reviewing the tutorial below on how to install Ubuntu 14.04, I would think Ubuntu Studio would be the same.  This should give you more details on what to do and expect during an installation.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by adiva on 2015-10-12
Try using "sudo gnome-disks", select device and choice "mount". It worked!

---

### Post by sudodus on 2015-10-12
If it is OK to overwrite alias 'format' the pendrive, I suggest that you use mkusb according to these links

[mkusb/gui#Installation](https://help.ubuntu.com/community/mkusb/gui#Installation)

[mkusb#Wipe_menu](https://help.ubuntu.com/community/mkusb#Wipe_menu)

If you want a standard file system for a pendrive, select the first option in the wipe menu,

"Standard: create MSDOS partition table with FAT32 partition"

---

