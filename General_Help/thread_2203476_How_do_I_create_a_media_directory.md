---
title: "How do I create a media directory"
date: 2014-02-03
forum: General Help
---

### Post by Photobug on 2014-02-03
I have a spare hard drive in my computer that I have partitioned to be specifically for storing of movies and music.  How do I create a directory on it for this purpose and how do I direct the files I want to be placed there?

---

### Post by grahammechanical on 2014-02-03
Are the partitions on that drive formatted? You should see the partitions in File Manager. If you select the partition and right click you should get a menu. Now select Properties and the Permissions tab and you will see that only Root has the authority to create and delete files. You will see a message: "You are not the owner, so you cannot change these permissions." This is the problem.

Now it all depends upon which version of Ubuntu you are using. Open a terminal and run

```
gksudo nautilus
```

After putting in your password File Manager will load with Root or Administrator authority. Now if you open the partition's Properties Permission tab you will see that the owner is now called "me." and you can now change the access for Group and Others from Access Files to Create and Delete Files. That should allow you to Create folders in that partition in the same way that you create folders inside /home. In other words by using File Manager when it is in normal or standard user mode.

If you are using Ubuntu 13.10 you may find that the command does not work because gksu is not installed. Run

```
sudo apt-get install gksu
```

Now you should be able to run that first command.

Regards.

---

### Post by ajgreeny on 2014-02-03
What filesystem is the drive formatted as;  ext#, ntfs, fat32?  This will determine how you can automount the partition as read/write by making an edit in your /etc/fstab file, and the partition and its folder(s) can then be linked into your /home

---

### Post by SeijiSensei on 2014-02-03
It sounds like you are starting with an empty partition.

If you use Ubuntu full time, I'd recommend putting an ext4 filesystem on the disk.  If you are dual-booting into Windows, I'd use NTFS instead.  You can use a GUI program like gparted for this or just type commands in a terminal session.  Here's how.

Let's start with the all-Linux method. Open a terminal and type:
```
sudo fdisk -l
```
That will give you an inventory of all the partitions on all your drives.  Let's assume that the drive in question is the second one in your system, which Linux calls /dev/sdb.  If you have partitioned this device, it will contain partitions with device names like /dev/sdb1.  If you created that partition and left it empty, it will need to have a "file system" installed first.  Unlike Windows, Linux commonly supports a wide variety of "filesystems" from its native ext to Windows NTFS, Mac HFS+, XFS, etc., along with various "network" file systems like NFS and CIFS.  If this machine will be running Linux nearly all the time, you should create an ext4 filesystem.  If you expect to boot regularly into Windows, see the NTFS discussion below. Otherwise, run the command
```
sudo mkfs -t ext4 /dev/sdb1
```
to create an "ext4" file system on the first partition ("1") of the second hard drive ("b"). Modify these as required.  This is the Linux equivalent to "formatting" the device for use.

Now you just need a place in the system's directory tree where you can "mount" the new file system.  Creating a directory below /media is preferred choice for applications like yours. Let's suppose we create "/media/storage" and attach the new file system there:
```

sudo mkdir /media/storage
sudo mount /dev/sdb1 /media/storage

```
You can now access the device by navigating to /media/storage either in a terminal or with a GUI file manager like Nautilus or Dolphin.

If you want to automate the process of mounting the drive so it is always available after a reboot, you need to edit the file **/etc/fstab** with root permissions using an editor like nano or gedit.  There are two ways to refer to partitions in fstab, either by device names like /dev/sdb1 or by "UUID" identifiers which are unique to each partition.  Using UUIDs helps if you switch drives in and out since you can be sure the correct partition is being mounted regardless of how Linux enumerates the devices.  If you run the command **blkid** at the prompt, you'll get a list of the UUIDs for all the partitions on your system.  In my case, the partition mounted as /dev/sdb1 appears in blkid like this:
```
/dev/sdb1: UUID="5253c7cc-fd70-4148-a3ae-77b64440bb8e" TYPE="ext4" 
```
I have this corresponding entry in /etc/fstab:
```
UUID=5253c7cc-fd70-4148-a3ae-77b64440bb8e /media/storage ext4 defaults  0 2
```
Note that the UUID is not enclosed in quotation marks in /etc/fstab.  For the meanings of the fields, read [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

If you want to use this directory with Windows as well as Linux, then you should create an **NTFS** file system on the partition.  Do this by using Windows own formatting utility.  Then create the directory /media/storage as before and add a line to /etc/fstab like this:
```
UUID=B6E681C3E68383F9 /media/storage ntfs defaults,umask=007,gid=46 0 0
```
This is the default Ubuntu mounting for a Windows partition.  It gives read/write/list rights to user root and members of group 46, the "plugdev" group, which by default includes the user with sudo rights ("grep 46 /etc/group" shows the group's members).  You can add users to that group or you can use an entirely different set of [permissions]("https://help.ubuntu.com/community/FilePermissions").  Setting umask=000 gives read/write/list rights to everybody for instance. You can omit the gid parameter in that case.

---

### Post by Photobug on 2014-02-03
Thanks for all the info so far.  I am typing this on my windows laptop.  The Ubuntu is set up on a separate computer running to run as an HTPC using XBMC.  I set it up using help from this forum and it is set up pretty much right but once XBMC was running i neglected the Ubuntu portion of the configuration.  At one point I even understood the terminal and some of the procedures but seem to have forgotten it all in the last 2 months.

The computer has 3 hard drives with many partitions but is setup to be able to run Ubuntu primarily and I believe the partions I am trying to use for this are ext4.  When I look at it, it looks like there may even be a /media directory on it and some files.  I will run and fdisk on the Ubuntu computer in a bit and post it here.  When I do do that how do I format the results to post here so it looks like I know what I am doing?

---

### Post by Photobug on 2014-02-03
In this computer I have 3 hard drives

[LIST=1]
[*]A 250GB HDD I used to experiment with Ubuntu setup it stil has an Ubuntu 12.04 installed on it.
[*]A 128GB ssd which is what I run Ubuntu 12.04 on which I believe is sdc/2
[*]A 500GB HDD that I partitioned into nearly equal halves.  I want to keep my media on one of both of these partitions.
[/LIST]
 
jordan@jordan-H67MA-UD2H-B3:~$ sudo fdisk -l
[sudo] password for jordan: 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8b550c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *    61442048   471042047   204800000    7  HPFS/NTFS/exFAT
/dev/sdb2       471042048   976773119   252865536    b  W95 FAT32

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b5f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480178175   240088064   83  Linux
/dev/sda2       480180222   488396799     4108289    5  Extended
/dev/sda5       480180224   488396799     4108288   82  Linux swap / Solaris

Disk /dev/sdc: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00058978

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    61442047    30720000    7  HPFS/NTFS/exFAT
/dev/sdc2   *    61442048   100925439    19741696   83  Linux
/dev/sdc3       112644094   250068991    68712449    5  Extended
/dev/sdc5       112644096   133124095    10240000   83  Linux
/dev/sdc6       139268096   155652095     8192000   83  Linux
/dev/sdc7       159752192   250068991    45158400    b  W95 FAT32
/dev/sdc8       155654144   159750143     2048000   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdh: 61.9 GB, 61872793600 bytes
32 heads, 63 sectors/track, 59943 cylinders, total 120845300 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x38ed3d19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          63   120845087    60422512+   7  HPFS/NTFS/exFAT
jordan@jordan-H67MA-UD2H-B3:~$

---

### Post by mastablasta on 2014-02-04
holy moly that's a compelx partitioning scheme. i woudl put all media on one big partition and then divide it into subfolders since xbmc reads from folders anyway. i have 2TB drive with only one parittion and then all stuff is in subfolders. in xbmc you asign folders for movies, folders for tv shows, pictures, videos etc.

note media directory on system disk is actually where external drives and such get mounted.

you 500 GB drive is formated part as NTFS the other part as FAT32.
/dev/sdb1 * 61442048 471042047 204800000 7 HPFS/NTFS/exFAT
/dev/sdb2 471042048 976773119 252865536 b W95 FAT32


do you want this to be automounted on boot as it is currently set?

---

### Post by Photobug on 2014-02-04
> **mastablasta said:**
> holy moly that's a compelx partitioning scheme. 

Yes it is.  I was initially going to try to dual boot this with Windows and wanted options to boot and store things for each system as well as options to experiment with alternative setups of Ubuntu or Linux.  So I assigned this for future options for growth.  Unfortunately I can't remember some of my passwords so may have to start over from scratch.


> **mastablasta said:**
> holy moly that's a compelx partitioning  scheme. i woudl put all media on one big partition and then divide it  into subfolders since xbmc reads from folders anyway. i have 2TB drive  with only one parittion and then all stuff is in subfolders. in xbmc you  asign folders for movies, folders for tv shows, pictures, videos etc.

note media directory on system disk is actually where external drives and such get mounted.

you 500 GB drive is formated part as NTFS the other part as FAT32.
/dev/sdb1 * 61442048 471042047 204800000 7 HPFS/NTFS/exFAT
/dev/sdb2 471042048 976773119 252865536 b W95 FAT32


do you want this to be automounted on boot as it is currently set?

Yes that is exactly why I am trying to do this, to automount it and then make it accessible to XBMC to store and access folders for movies, tv shows and music.  I have a whole separate computer for my photos.  Once I have this figured out I will be creating a separate server but want to configure this 500 GB for storage until then.  Is there a way to make this all one drive now without loosing the info on it?

---

### Post by SeijiSensei on 2014-02-04
No, you'll lose everything if you repartition the device.

Just try this:
```

sudo mkdir /mnt/win1 /mnt/win2
sudo mount /dev/sdb1 /mnt/win1
sudo mount /dev/sdb2 /mnt/win2

```
(I'm using /mnt since that is now considered to be the place for temporary mounts.)  Now you'll see the contents of each partition in the win1 and win2 folder.  Once you've decided what you want to do, you can create a mount point like /media/storage, mount one or the other partition there, and add the appropriate entry to /etc/fstab.  If you choose to use /dev/sdb2 and want to leave it as FAT32, the entry in /etc/fstab would read:
```
/dev/sdb2 /media/storage vfat defaults 0 2
```
or the equivalent with UUID=.  I'll warn you that FAT32 partitions have a maximum file size limit of 4 GB, less even than a full DVD ISO image.  Some media files can easily be bigger than 4 GB.  If you will be storing files this large or larger, you should choose either ext4 or NTFS as the file system rather than FAT32.

---

