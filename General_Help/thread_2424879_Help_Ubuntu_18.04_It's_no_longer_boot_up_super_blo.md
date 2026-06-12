---
title: "Help Ubuntu 18.04 It's no longer boot up super block corrupt"
date: 2019-08-16
forum: General Help
---

### Post by Gadget2008 on 2019-08-16
I ran Ubuntu Linux 18.04 from 126gb SanDisk USB flash drive and recently I can't boot up and recovery mode doesn't help much.I spent a few hours to try fix run different commands, technique but I still can't boot up.I got some important data on this drive. Also I can't access this drive any more.
If anyone can help me I will be very grateful for help.
I provide some pictures of my problem.Please have a look and try to help me.
I try GParted to fix this drive and that's outcome I pasted below:
,,GParted 0.30.0 --enable-libparted-dmraid --enable-online-resize

Libparted 3.2
Check and repair file system (ext4) on /dev/sda1  00:00:00    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1 (partition)
start: 2048
end: 240252927
size: 240250880 (114.56 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
e2fsck -f -y -v -C 0 '/dev/sda1'  00:00:00    ( ERROR )
     	
Disk write-protected; use the -n option to do a read-only
check of the device.
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: Read-only file system while trying to open /dev/sda1
libparted messages    ( INFO )
     	
Unable to open /dev/sda read-write (Read-only file system). /dev/sda has been opened read-only.
Unable to open /dev/sda read-write (Read-only file system). /dev/sda has been opened read-only.

Thank you for reading.

---

### Post by Autodave on 2019-08-16
Generally speaking, if the super block is corrupt, you are unlikely to save anything that is on that drive be it a HD, SSD, or thumb drive. That usually means that the drive has failed.  However, the super block could have been corrupted by a write error in which case reformatting it may save it.  You will erase everything on it during the reformat.

One last hope....and this is a slim hope......try booting your machine with a different medium and see if you can access the drive and recover any files.

---

### Post by joris_donders2 on 2019-08-16
Just make a new, small 4gb drive or so, and create a bootable stick. 

now, plug both drives and save out data as much as you can on your HDD of the computer. 

The SSD Flash drive will have a corrupt superblock; nothing you can do about it ........ just, after saving your data, format it again and do a fresh ISO on it : who knows you'll have no problems anymore. 

USB flash drives may be a solution: I would disadvise it for running an OS regurlary on it. Just because of the inner tech of those drives ...... 

Anyway just create a small bootable stick and hope for the best ... 

Fingers crossed.

---

### Post by haplorrhine on 2019-08-16
"Impossible" might be used hastily.
[https://en.wikipedia.org/wiki/Data_recovery](https://en.wikipedia.org/wiki/Data_recovery)

---

### Post by oldfred on 2019-08-16
First make sure you have backups.
And major repair like this may create more issues & data is totally lost.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

      
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

