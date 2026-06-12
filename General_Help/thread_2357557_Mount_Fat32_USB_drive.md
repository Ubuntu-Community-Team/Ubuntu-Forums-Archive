---
title: "Mount Fat32 USB drive"
date: 2017-04-03
forum: General Help
---

### Post by 443355-costello on 2017-04-03
I am trying to mount a 4Terrabyte USB hard drive to a 64 bit Dell machine running Ubuntu.  When I pug it in, I get this error:
"   	 	 	 	   Error mounting /dev/sdb1 at /media/costello/Fat Boy: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/costello/Fat Boy"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

  
"
I would really appreciate help with this so that I can transfer all my files and have Linux be my primary operating system.  I have a Windows machine and a mac that can recognize the hard drive, Fat Boy.


Here is some other diagnostic data:
  	 	 	 	   costello@costello-Linux-Lappy:~$ cat /var/log/installer/media-info
 Ubuntu 16.04.2 LTS "Xenial Xerus" - Release amd64 (20170215.2)costello@costello-
 
 
 costello@costello-Linux-Lappy:~$ sudo blkid
 /dev/sda1: UUID="c812d772-617c-46df-bf12-15efbad38e8f" TYPE="ext4" PARTUUID="d8f93a17-01"
 /dev/sda5: UUID="0df37207-9822-4566-8dcb-f620b45083f4" TYPE="swap" PARTUUID="d8f93a17-05"
 /dev/sdb1: LABEL="Fat Boy" UUID="5456-81A0" TYPE="exfat"
 
 
 costello@costello-Linux-Lappy:~$ df
 Filesystem     1K-blocks    Used Available Use% Mounted on
 udev             1963768       0   1963768   0% /dev
 tmpfs             396992    6444    390548   2% /run
 /dev/sda1      118885644 6183396 106640120   6% /
 tmpfs            1984944     200   1984744   1% /dev/shm
 tmpfs               5120       4      5116   1% /run/lock
 tmpfs            1984944       0   1984944   0% /sys/fs/cgroup
 tmpfs             396992      56    396936   1% /run/user/1000

---

### Post by oldfred on 2017-04-03
Not sure about ex-FAT. That is a proprietary Microsoft format.
But there now is an exFat driver. It may not be installed by default.

sudo apt-get update
sudo apt-get install exfat-fuse exfat-utils

But if drive was used by Windows 8 or Windows 10 without turning off the always on hibernation which keeps all partitions mounted, your partition may still look like it is mounted. The Linux drivers will not normally mount in read/write mode. You may be able to manually mount in read only mode. Not sure of exact command with exfat.

Also some large drives that should be gpt partitioned have some weird ways of partitioning that can cause issues.
Also some external drive caddies have issue with drives over 2TiB or gpt partitioned.

---

### Post by 443355-costello on 2017-04-03
# The first command seemed to work and ended with:
Fetched 3,963 kB in 5s (769 kB/s)                                     
Reading package lists... Done

# The second command did not seem successful:
costello@costello-Linux-Lappy:~$ sudo apt-get install exfat-fuse exfat-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fuse-exfat

---

### Post by ajgreeny on 2017-04-03
The package is exfat-fuse, not fuse-exfat.
Try that and it should work.

---

### Post by oldfred on 2017-04-03
Thanks ajgreeny.
Teach me not to look it up and just try to type it.

---

### Post by 443355-costello on 2017-04-04
I did this:

   costello@costello-Linux-Lappy:~$  sudo apt-get install exfat-utils exfat-fuse
 [sudo] password for costello:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following NEW packages will be installed:
   exfat-fuse exfat-utils
 0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
 Need to get 64.9 kB of archives.
 After this operation, 281 kB of additional disk space will be used.
 Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 exfat-fuse amd64 1.2.3-1 [24.8 kB]
 Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 exfat-utils amd64 1.2.3-1 [40.1 kB]
 Fetched 64.9 kB in 0s (126 kB/s)        
 Selecting previously unselected package exfat-fuse.
 (Reading database ... 217362 files and directories currently installed.)
 Preparing to unpack .../exfat-fuse_1.2.3-1_amd64.deb ...
 Unpacking exfat-fuse (1.2.3-1) ...
 Selecting previously unselected package exfat-utils.
 Preparing to unpack .../exfat-utils_1.2.3-1_amd64.deb ...
 Unpacking exfat-utils (1.2.3-1) ...
 Processing triggers for man-db (2.7.5-1) ...
 Setting up exfat-fuse (1.2.3-1) ...
 Setting up exfat-utils (1.2.3-1) ...


But now I still get nothing. I got the same error message when I connected the hard drive.  So, I rebooted the computer.  Nothing.  The Disks utility doesn't see it.  My Windows computer can see it.  The USB port works.   Thank you for reading and helping.

---

### Post by sudodus on 2017-04-04
In order to help us help you, please post the output of the following commands

```
sudo lsblk -f
sudo lsblk -m
```

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

