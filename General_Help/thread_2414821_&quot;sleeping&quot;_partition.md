---
title: "&quot;sleeping&quot; partition?"
date: 2019-03-15
forum: General Help
---

### Post by otsuriver on 2019-03-15
Not sure if it is the appropriate title but let me explain.

I have one hard disk, partitioned in two (the partitioning was made by Lubuntu installer). I installed Lubuntu in partition 1, and left partition 2 for my data. So far so good, installation was successful and I love Lubuntu.

I created a link in the desktop which takes me to an application in the partition 2. But it doesnt work (the systems asks which application should it use to open the link file!! (not the LINKED file, but the shortcut iself!). So I open the file using file manager, and then the shurtcut start working!

It looks like the partition 2 needs to be accessed once by the system before any shortcut to it works. 

Any idea?

---

### Post by oldos2er on 2019-03-15
If I'm understanding you correctly, you need the second partition mounted at system startup. To do this you need to edit your /etc/fstab; see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by oldfred on 2019-03-15
If internal drive, you would want to mount the partition in fstab, so always mounted & mounted at same place every time.
I have multiple Ubuntu installs, so so not want to share /home as I may want separate settings to test something, but do want all the same data.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below. 
   The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) & 
[https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk](https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by otsuriver on 2019-03-17
Thanks a lot for your replies.

Yes, in partition 1 I have only Lubuntu installed, no dual boot or multiple installations, just one simple Lubuntu in partition 1, my data in partition 2. 

From your replies I learned about this and It sounds reasonable that the problem is that **the partition only auto-mounts first time it is accessed**, and the 1st time has to be (or is, at least in my current setup) by the file manager. This would explain that once I access it with the file manager I can access it with other programs and shortcuts from then on.  

 So, I would like to try editing the fstab but I don't dare doing it without asking. Too many times I have screwed things and had to reinstall because I didn't pay attention to "details" so I would like if you can confirm that the following addition to my fstab would be OK (or at least that I will not make my partition inaccessible or broken -- it my data partition so it is the most valuable).

 
Here is some (hopefully relevant) information I got when reading some of the URL you guys suggested:

 
 
 ```
--- start of fstab file ---

 # /etc/fstab: static file system information.
 #
 # Use 'blkid' to print the universally unique identifier for a device; this may
 # be used with UUID= as a more robust way to name devices that works even if
 # disks are added and removed. See fstab(5).
 #
 # <file system> <mount point> <type> <options> <dump> <pass>
 UUID=94a3f691-a94a-4722-a80c-8fd0d59f4fe9 / ext4 defaults 0 1
 --- end of fstab file ---

``` 
And the output of some various commands to help you help me :p  

 ```
--- start terminal history ----

 user00@mypc:~$ ls /dev/disk/by-label -lah
 total 0
 drwxr-xr-x 2 root root 60 Mar 16 11:33 .
 drwxr-xr-x 7 root root 140 Mar 16 11:33 ..
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 r.all -> ../../sda2
 user00@mypc:~$ ls /dev/disk/by-id -lah
 total 0
 drwxr-xr-x 2 root root 200 Mar 16 11:33 .
 drwxr-xr-x 7 root root 140 Mar 16 11:33 ..
 lrwxrwxrwx 1 root root 9 Mar 16 11:34 ata-HL-DT-ST_DVDRAM_GUC0N_KWHF56F5036 -> ../../sr0
 lrwxrwxrwx 1 root root 9 Mar 16 11:34 ata-ST1000LM024_HN-M101MBB_S32XJ9EG926473 -> ../../sda
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 ata-ST1000LM024_HN-M101MBB_S32XJ9EG926473-part1 -> ../../sda1
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 ata-ST1000LM024_HN-M101MBB_S32XJ9EG926473-part2 -> ../../sda2
 lrwxrwxrwx 1 root root 9 Mar 16 11:34 wwn-0x50004cf210a76d27 -> ../../sda
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 wwn-0x50004cf210a76d27-part1 -> ../../sda1
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 wwn-0x50004cf210a76d27-part2 -> ../../sda2
 lrwxrwxrwx 1 root root 9 Mar 16 11:34 wwn-0x5001480000000000 -> ../../sr0
 user00@mypc:~$ ls /dev/disk/by-uuid -lah
 total 0
 drwxr-xr-x 2 root root 80 Mar 16 11:33 .
 drwxr-xr-x 7 root root 140 Mar 16 11:33 ..
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 94a3f691-a94a-4722-a80c-8fd0d59f4fe9 -> ../../sda1
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 96782954-2c88-4c7a-87d1-f42396d80456 -> ../../sda2
 user00@mypc:~$ sudo fdisk -l
 [sudo] password for user00:  
 Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0x63f35bc3
 

 
 Device Boot Start End Sectors Size Id Type
 /dev/sda1 108544 297068543 296960000 141.6G 83 Linux
 /dev/sda2 297068544 1953519615 1656451072 789.9G 83 Linux
 

 
 

 
 

 
 

 
 Disk /dev/zram0: 984.6 MiB, 1032454144 bytes, 252064 sectors
 Units: sectors of 1 * 4096 = 4096 bytes
 Sector size (logical/physical): 4096 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 

 
 

 
 Disk /dev/zram1: 984.6 MiB, 1032454144 bytes, 252064 sectors
 Units: sectors of 1 * 4096 = 4096 bytes
 Sector size (logical/physical): 4096 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 

 
 

 
 Disk /dev/zram2: 984.6 MiB, 1032454144 bytes, 252064 sectors
 Units: sectors of 1 * 4096 = 4096 bytes
 Sector size (logical/physical): 4096 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 

 
 

 
 Disk /dev/zram3: 984.6 MiB, 1032454144 bytes, 252064 sectors
 Units: sectors of 1 * 4096 = 4096 bytes
 Sector size (logical/physical): 4096 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 user00@mypc:~$ ls /dev/disk/by-uuid -alh

 total 0

 drwxr-xr-x 2 root root 80 Mar 16 11:33 .
 drwxr-xr-x 7 root root 140 Mar 16 11:33 ..
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 94a3f691-a94a-4722-a80c-8fd0d59f4fe9 -> ../../sda1
 lrwxrwxrwx 1 root root 10 Mar 16 11:34 96782954-2c88-4c7a-87d1-f42396d80456 -> ../../sda2
 user00@mypc:~$  
  --- end terminal history ----

``` 
 
 So I assume I have to add one line to my fstab file, which should include the following:  
 ```
UUID=96782954-2c88-4c7a-87d1-f42396d80456 r.all ext4

 
```
but I am not sure what to use after that (I don't know the meaning of "defaults", "0", "1")  

 

 
 So I am correct, after editing I would have the following two lines in my fstab:
 ```
UUID=94a3f691-a94a-4722-a80c-8fd0d59f4fe9 / ext4 defaults 0 1

 UUID=96782954-2c88-4c7a-87d1-f42396d80456 r.all ext4 **? ? ?**


``` 
Where the **"?"** are the options I don't dare to copy from the 1st line and kindly ask for your suggestions :p

---

### Post by oldfred on 2019-03-17
You have to also create a mount point.
If you mount in /media it will be in the left panel with Naulitus, not sure with file browser in Lubuntu.
But if mounted in / or /mnt then it will not appear in Naulitus and you have to either drill down (up?) from root to find your files.
Default mount for temp mounts using file manager is /media/$USER/UUID or label. I always label all partitions so not mounted by UUID as I have some I do not mount with fstab. The $USER is your login name. 
fred@Bionic-Z170N:~$ echo $USER
fred

For lots more info on mounting & fstab see these:
man mount
man fstab

Not sure if r.all is valid name, do you have that already?
# Make permanent mount point (unmount if already mounted):
 sudo mkdir /media/r_all
# Find your UUID:
sudo blkid -c /dev/null -o list 

   sudo cp /etc/fstab /etc/fstab.backup
sudoedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a 

# Entry for /dev/sda2 :
      UUID=96782954-2c88-4c7a-87d1-f42396d80456  /media/r_all ext4 noatime 0 2

      [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 
    
If permission or ownership issues, you may need to reset those:
      
 # ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /media/r_all
# The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /media/r_all
# note that -R is recursion or all files & subfolders & files are changed. Never use on system folder or /, just on your data partition.

---

### Post by oldos2er on 2019-03-17
> I would like to try editing the fstab but I don't dare doing it without asking. Don't edit system files without first making a backup copy; this is a lesson I learned the hard way. So ```
sudo cp /etc/fstab /etc/fstab.backup
``` Think of it as insurance.

---

### Post by otsuriver on 2019-03-17
Thanks a lot guys, it works perfectly as expected now :razz:
I made the backup copy of fstab as suggested and then added a line to it.

> Not sure if r.all is valid name, do you have that already?
Yes, I had that already.

> # Entry for /dev/sda2 :
      UUID=96782954-2c88-4c7a-87d1-f42396d80456  /media/r_all ext4 noatime 0 2
It didn't work like that, but I realized the cause and I actually **modified** it to
> # Entry for /dev/sda2 :
      UUID=96782954-2c88-4c7a-87d1-f42396d80456  /media/**user00/**r.all ext4 noatime 0 2

So this is the current content of my  fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=94a3f691-a94a-4722-a80c-8fd0d59f4fe9 /              ext4    defaults   0 1
UUID=96782954-2c88-4c7a-87d1-f42396d80456 /media/user00/r.all ext4 noatime 0 2
```

THANKS!!!

---

