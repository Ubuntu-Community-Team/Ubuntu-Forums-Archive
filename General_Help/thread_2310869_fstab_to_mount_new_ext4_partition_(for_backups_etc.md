---
title: "fstab to mount new ext4 partition (for backups etc)"
date: 2016-01-22
forum: General Help
---

### Post by Kris_M on 2016-01-22
I created a new ext4 partition on a different spindle from 14.04.3.
I want to use it for backups and whatever.
I test mounted it via terminal and copied a folder to it and was able to open the folder. (but I could not add new folders to it)
I added "/dev/sdb2 /work1 ext4 defaults 0 2" to /etc/fstab (without quotes) but on reboot it does not mount it.
gparted finds it at that address.

---

### Post by Kris_M on 2016-01-22
oh duh - /home/name/work1
but owner is root - need to change owner

EDIT - NO - needs to be /work1 - otherwise I will backup all of work1
needs to be able to automatically mount like my ntsf partitions do.

---

### Post by deadflowr on 2016-01-22
Use the UUID instead, works better imo.
run
```
sudo blkid
```
locate the partition and copy the UUID number.
then in fstab add the number preceded by UUID=
like
```
UUID=9042390479427332947243 /work1 ext4 default 0 2
```
uuid's stay the same regardless of where the device is in relation to the machine or OS.''

Edit: I see you figured out the location error.

---

### Post by oldfred on 2016-01-22
I create mount point & manually mount once to make it available and change ownership & permissions. Then I add it to fstab.

       #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by Kris_M on 2016-01-22
EDIT later<snip> I screwed up and caused myself a 2 hour timeout repairing stuff - LOL

Later tater

Thanks for trying to help all!!!!

---

### Post by Kris_M on 2016-01-22
No, needs to be /work  needs to mount automatically like my ntfs partitions do, and they aren't in fstab.

---

### Post by Kris_M on 2016-01-22
@oldfred, I did 
```
kris@kris-Z87N-WIFI:~$ sudo blkid
[sudo] password for kris: 
/dev/sda1: LABEL="System Reserved" UUID="01CF079EC34F1200" TYPE="ntfs" 
/dev/sda2: LABEL="Cwin7" UUID="01CF079F6738BD80" TYPE="ntfs" 
/dev/sda5: UUID="370936c1-9242-499c-a545-d505d5002bc5" TYPE="ext4" 
/dev/sda6: UUID="86dac6d5-4d7b-4e79-a934-4e82531b650b" TYPE="swap" 
/dev/sda7: LABEL="E" UUID="2CBC5723BC56E6BC" TYPE="ntfs" 
/dev/sdb1: LABEL="extHG1T" UUID="01D1550FFBB41AD0" TYPE="ntfs" 
/dev/sdb2: LABEL="work1" UUID="d2444225-e665-45d1-b318-2d5280ab8d18" TYPE="ext4" 
kris@kris-Z87N-WIFI:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  387MB   386MB   primary   ntfs            boot
 2      387MB   63.3GB  62.9GB  primary   ntfs
 3      63.3GB  212GB   149GB   extended                  lba
 5      63.3GB  135GB   71.3GB  logical   ext4
 6      135GB   142GB   7463MB  logical   linux-swap(v1)
 7      142GB   212GB   70.2GB  logical   ntfs


Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  519GB   519GB  primary  ntfs
 2      519GB   1000GB  481GB  primary  ext4


kris@kris-Z87N-WIFI:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="01CF079EC34F1200" TYPE="ntfs" 
/dev/sda2: LABEL="Cwin7" UUID="01CF079F6738BD80" TYPE="ntfs" 
/dev/sda5: UUID="370936c1-9242-499c-a545-d505d5002bc5" TYPE="ext4" 
/dev/sda6: UUID="86dac6d5-4d7b-4e79-a934-4e82531b650b" TYPE="swap" 
/dev/sda7: LABEL="E" UUID="2CBC5723BC56E6BC" TYPE="ntfs" 
/dev/sdb1: LABEL="extHG1T" UUID="01D1550FFBB41AD0" TYPE="ntfs" 
/dev/sdb2: LABEL="work1" UUID="d2444225-e665-45d1-b318-2d5280ab8d18" TYPE="ext4" 
kris@kris-Z87N-WIFI:~$ sudo mkdir /mnt/data
kris@kris-Z87N-WIFI:~$ sudo mount /dev/sdb2 /mnt/data
kris@kris-Z87N-WIFI:~$ sudo chmod -R a+rwX,o-w /mnt/data
kris@kris-Z87N-WIFI:~$ sudo chown -R $USER:$USER /mnt/data
kris@kris-Z87N-WIFI:~$ 
```

and rebooted and all is well!!!  and backupdeja is backing up

no mod to fstab which is fine since my ntsb partitions don't have any entry there either.

_**[SIZE=6]THANKS!!!!!![/SIZE]**_

---

### Post by oldfred on 2016-01-22
Ownership & permissions are important. But best to automount with fstab.

I did not mount my backup partition and have a script to run rsync. In beginning I did not manually mount it once and it defaulted to / instead of where I wanted it. Fortunately I had room or it would have been a huge issue. Now my backup script auto-mounts backup partition.

---

### Post by Kris_M on 2016-01-22
will do
should i use
"/dev/sdb2 /work1 ext4 defaults 0 2"

Got a 3hr d/l going so will test later.

---

### Post by oldfred on 2016-01-22
Much better to use UUIDs as deadflowr posted above.

Drives can change. On both my systems I managed not to use first SATA port when building them. And flash drive then seemed to get in before one or more of the SATA drives. And then flash drive became sdb and sdb became sdc, but UUIDs did not change.

---

### Post by Kris_M on 2016-01-22
so
UUID=d2444225-e665-45d1-b318-2d5280ab8d18 /work1 ext4 defaults 0 2

?
(don't want to visit xenial again... :D )

my current fstab is
```
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=370936c1-9242-499c-a545-d505d5002bc5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=86dac6d5-4d7b-4e79-a934-4e82531b650b none            swap    sw              0       0

```

---

### Post by oldfred on 2016-01-22
After you edit fstab, run this, if not errors then ok. Make sure unmounted first.

       sudo mount -a
    
I have seen this 
 defaults,noatime
And I use this
relatime

The use of noatime is now suggested for SSD to reduce the write of inode time on every access to reduce writes. Also news servers per man mount. But a very few apps(mutt) may have issues.

Per man mount:
 > relatime
              Update inode access times relative to  modify  or  change  time.
              Access time is only updated if the previous access time was ear&#8208;
              lier than the current modify or change time. (Similar  to  noat&#8208;
              ime,  but  doesn't break mutt or other applications that need to
              know if a file has been read since the last time  it  was  modi&#8208;
              fied.)

              Since Linux 2.6.30, the kernel defaults to the behavior provided
              by this option (unless noatime was  specified), and the stricta&#8208;
              time  option  is  required  to  obtain traditional semantics. In
              addition, since Linux 2.6.30, the file's  last  access  time  is
              always  updated  if  it  is more than 1 day old.



 Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

---

### Post by Kris_M on 2016-01-22
Thanks.
I used relatime, since it is HD, but on reboot the partition no longer shows on the left side and I assume the only way I can access it is through terminal.
I need the convenience of having it show in the file manager windows.
So I deleted the line.

---

### Post by Dennis N on 2016-01-22
> **Kris_M said:**
> Thanks.
I used relatime, since it is HD, but on reboot the partition no longer shows on the left side and I assume the only way I can access it is through terminal.
I need the convenience of having it show in the file manager windows.
So I deleted the line.
The terminal is not needed to access your data. A way to have a partition mount in fstab and also be conveniently available in the file manager side pane is to create a bookmark, and that location will be available in Places. See screenshot attached. Under Places, Common-Files is really (the root of) a file system on a separate partition.

---

### Post by Kris_M on 2016-01-22
I do not see how to make a bookmark of it if it's not showing.
And as a bookmark it is only available in file mgr window, not on desktop, unless I am missing something...

---

### Post by Dennis N on 2016-01-22
> **Kris_M said:**
> I do not see how to make a bookmark of it if it's not showing.
And as a bookmark it is only available in file mgr window, not on desktop, unless I am missing something...

Well, to make the bookmark, I just browse with the file manager to the mount point of the other partition. Then, somewhere in your file manager menus is an option to create a bookmark (it also may use the term shortcut) for the folder you viewing. Often if you right-click on the mount point folder, there is also an option to make a bookmark or shortcut. I am sure Ubuntu's file manager can do it.

---

### Post by Kris_M on 2016-01-22
Ah - "I just browse with the file manager to the mount point of the other partition"  I don't know how to do that...

---

### Post by Dennis N on 2016-01-22
The other partition mounts at /work? Your browser side pane should show some description like  "Computer" or "File System" ( see image of post #14) which should get you to /. Your mount folder /work will be a subfolder of /. Or, you can start at your home folder and go up two levels to /. Then you will see /work as a subfolder of /.

---

### Post by Kris_M on 2016-01-22
when I click on computer I can only go up 1 level and that's home

I have no side panel icon named computer.

---

### Post by Dennis N on 2016-01-22
> **Kris_M said:**
> when I click on computer I can only go up 1 level and that's home

I have no side panel icon named computer.

Here is a tutorial on how to bookmark a folder to study. It uses Ubuntu 14.04 and should work for you. Under Devices, it does show "Computer".

[http://www.howtogeek.com/193777/beginner-how-to-add-a-bookmark-to-a-location-in-nautilus-files-in-ubuntu-14.04/](http://www.howtogeek.com/193777/beginner-how-to-add-a-bookmark-to-a-location-in-nautilus-files-in-ubuntu-14.04/)

---

### Post by Kris_M on 2016-01-22
Thanks!  I'll have a look!!!  :D

---

### Post by Kris_M on 2016-01-23
okay, finally got a chance to look at it - 
YES, got it -  THANKS! :D
put line back in fstab.  
"UUID=d2444225-e665-45d1-b318-2d5280ab8d18 /work1 ext4 relatime 0 2" (without quotes)(this is a 1T HD(spindle))
easy way to get to " /"  is, in Nautilus(file manager) (way up at top left of screen) "go" / "enter location" (type / and hit enter - voila)
then double click on work1 (or whatever) and way up at top left click on "bookmarks" / "bookmark this location"  

Shows as bookmarks, not places (14.04.3 Unity)

Now, tell me what is the advantage to doing it this way, because oldfred wanted me to do it this way, too. (?)

THANKS!!!

---

### Post by Kris_M on 2016-01-23
> **deadflowr said:**
> Use the UUID instead, works better imo.
run
```
sudo blkid
```
locate the partition and copy the UUID number.
then in fstab add the number preceded by UUID=
like
```
UUID=9042390479427332947243 /work1 ext4 default 0 2
```
uuid's stay the same regardless of where the device is in relation to the machine or OS.''

Edit: I see you figured out the location error.

Huge thanks for this!!!  used it!!!!!!!

---

### Post by oldfred on 2016-01-23
I prefer to mount in /mnt/data. And only have folders at top level in that data partition. But with Linux and your own system you can mount just about anywhere and have it work.

And then I link all folders in /mnt/data into /home replacing Documents, Videos, Music, etc and adding a few of my own. Then links are in /home, but /mnt/data is not. On occassion when I do need that path I do have to go into computer or system to get to it.

I use a shared data partition primary as I have multiple installs and want to see same data in all of them. I also did the same with another data partition as NTFS, when using XP, but not any more.
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Kris_M on 2016-01-23
Thanks!  So it's a "preference" thing rather than a "performance" thing?

---

### Post by Kris_M on 2016-01-23
> **oldfred said:**
> I prefer to mount in /mnt/data. And only have folders at top level in that data partition. But with Linux and your own system you can mount just about anywhere and have it work.

And then I link all folders in /mnt/data into /home replacing Documents, Videos, Music, etc and adding a few of my own. Then links are in /home, but /mnt/data is not. On occassion when I do need that path I do have to go into computer or system to get to it.

I use a shared data partition primary as I have multiple installs and want to see same data in all of them. I also did the same with another data partition as NTFS, when using XP, but not any more.
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

While reading through these I realized I had another "problem" that I could go ahead and solve.  I looked at
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
I share the TBird mail folder between Ubuntu and Windows as it keeps me current no matter where I am.  Windows never hibernates. Only one or the other is ever active, never both. (only one computer and 2 hands)
  When I start TBird in Ubuntu, I need to have first clicked on the E partition to open and close it.  THEN TBird finds the folder and all is well.  Otherwise I kick myself, stop TBird, open E, and start TBird again and all is well.
   So I could mount it in fstab:
blkid gives:
/dev/sda7: LABEL="E" UUID="2CBC5723BC56E6BC" TYPE="ntfs" 
so:
sudo mkdir /media/E
and add this to fstab:
UUID=2CBC5723BC56E6BC /media/E ntfs-3g defaults,noatime,windows_names,locale=en_US.utf8  0 0
save fstab
sudo mount -a  to check

Does that seem reasonable - I used the recommendation from that site but added noatime since E is on my 250GB SSD (70gb)(along with my 70gb 14.04.3).

Thanks!!!

---

### Post by oldfred on 2016-01-24
I have seen this for NTFS:
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

And I edit profile.ini with correct path for where both Thunderbird and Firefox is.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Kris_M on 2016-01-24
There are apparently a lot of different ways that work.  The one I came up with
UUID=2CBC5723BC56E6BC /media/E ntfs-3g defaults,noatime,windows_names,locale=en_US.utf8  0 0
did in fact work - at least I have found no problems with it.  I will look at your links.
THANKS!!!!!  :D

---

### Post by Kris_M on 2016-01-25
> **oldfred said:**
> I have seen this for NTFS:
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

And I edit profile.ini with correct path for where both Thunderbird and Firefox is.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

each time I look at this stuff i understand it a little bit more...  Thanks for being patient!

THANKS!!!!!!!!!!

---

