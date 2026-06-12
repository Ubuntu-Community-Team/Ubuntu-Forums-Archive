---
title: "Can I choose to install 3rd party software elsewhere (Not w/Ubuntu)?"
date: 2016-12-21
forum: General Help
---

### Post by javierdl on 2016-12-21
Hi all,

This is the situation: I need to make space in my SSD where I have both Ubuntu and Win10 installed, with 3 accounts each.
I am setting out to remove some software to reinstall it in a partition (ext4) in an internal HD. Like Libre Office, Gimp, Blender, etc.
My question is: Will I be given the choice to choose such location during the installation? 
And, is there a disadvantage to do it this way?

Thanks guys,

JDL

---

### Post by TheFu on 2016-12-21
It depends on the installer for the software.  If it uses APT, no, you won't be asked.
I would move the user /home/ to a different disk, not the installation locations for packaged (.deb) files.

If you don't use APT, then there are all sorts of disavantages. Too many to list. APT is amazing for 50 reasons. Doing package installs manually, like we did in the 1990s, sucks.  Manually dealing with dependencies. Getting base packages stuck because some manually installed package won't allow update, having to manually do the updates ourselves ... basically, it would be like ... er ... Windows pkg management. Eeeewww.  

Package management is one of the main reasons I run Linux and not some other OS.

---

### Post by javierdl on 2016-12-21
Thank you TheFu :)
I suspected something like this.
I am so glad I asked ;)
Ok, then how do you [COLOR=#000000]move the user /home/ to a different disk ?

JDL[/COLOR]

---

### Post by TheFu on 2016-12-22
Most questions asked in these forums have answers.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

"Moving HOME directory" is the search that found this: [https://ubuntuforums.org/showthread.php?t=2182174](https://ubuntuforums.org/showthread.php?t=2182174)
[https://askubuntu.com/questions/21321/move-home-folder-to-second-drive](https://askubuntu.com/questions/21321/move-home-folder-to-second-drive)
[https://askubuntu.com/questions/239843/moving-home-user-directory-to-another-drive](https://askubuntu.com/questions/239843/moving-home-user-directory-to-another-drive)

---

### Post by javierdl on 2016-12-22
Cool!
I'll read that. Thanks a bunch TheFu :)

---

### Post by javierdl on 2017-01-07
Finally I had the chance to give this a try. And by the way, the whole objective is to reduce the space used in my SSD. Reason why it was recommended that I moved my home directory/ies elsewhere.
Unfortunately I clearly underestimated it, and now, although Ubuntu does load, and it does load enough to present our 3 accounts, that's as far as I can go :(
The password seems to be recognized, but it sort of flashes and brings me back to the same place where you are to enter your password :(
Basically I went to this [post]("https://ubuntuforums.org/showthread.php?t=2343317&p=13570363#post13570363"), where I'm advised to enter this command lines:
```
cd /
sudo mv home oldhome
sudo mkdir home
sudo mount /dev/sdb1 home 
```

I had to boot from a Live USB key though, as before it was telling me there were some open files and it would not give me access to do this.
So I located where everything was, and via the Terminal and with sudo, I used "mv" to bring the 3 folders representing my accounts from /home. To the partition where I have more space. Then just in case, I copied them back, as to have a backup if you will. 
Then I added the mounting line in etc/fstab to mount the new home directory I had added in the larger partition. I did create a copy of this fstab file just in case.
Basically this is how I got in trouble.
I did go back to that fstab file the same way (via the Live USB), to remove the new mounting line in the hope it would do, but nope! It was not enough.

I do understand I am leaving many details out, unfortunately I am at work at the moment. So I'll have to wait until later tonight to send more info, like the partition's IDs, the exact mounting text line, etc
However, if someone already has a fairly good idea of what could be the problem and what I should do, by all means post it :)

Thanks in advance,

JDL

---

### Post by javierdl on 2017-01-08
Ok, here is the environment data:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32           EF    boot, esp
 5      538MB   301GB   300GB   ext4
 2      301GB   615GB   315GB   ext4                  msftdata ([COLOR=#008000]Here is where I want to move the home directory to[/COLOR])
 3      615GB   992GB   377GB   ext4
 4      992GB   1000GB  8523MB  linux-swap(v1)        diag


Model: ATA Patriot Torch LE (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  211MB   210MB   fat32                 boot, esp
 2      211MB   228MB   16.8MB  ext4            Mi    msftres
 3      228MB   1026MB  799MB   ntfs                  msftdata
 4      1026MB  88.6GB  87.6GB  ntfs                  msftdata
 6      88.6GB  109GB   20.8GB  ext4 ([COLOR=#008000]this is where the etc/fstab file is[/COLOR])
 7      109GB   110GB   386MB   linux-swap(v1)
 8      110GB   120GB   10.3GB  ext4            sd8 ([COLOR=#008000]this is where the 3 accounts folders are[/COLOR])


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start  End     Size    Type     File system  Flags
 1      106MB  2000GB  2000GB  primary  ntfs


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? i
Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdd: 16.0GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags:

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1499MB  1501MB  2425kB               EFI


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: MATSHITA DVD-RAM SW840 (scsi)                                      
Disk /dev/sr0: 80.5MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags:


```


```


ubuntu@ubuntu:~$ sudo fdisk-lu
sudo: fdisk-lu: command not found

ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /rofs          
/dev/sda1  vfat             (not mounted)  D45B-1044
/dev/sda2  ext4    315gb    (not mounted)  90e8492c-c40d-44ea-a370-941cc17a6d2d
/dev/sda3  ext4    Partition_377 (not mounted) 1cc33a38-c617-4e9e-acf4-19c79415609e
/dev/sda4  swap             [SWAP]         e863d0f6-0ab2-4f1f-9fa3-55a652b02283
/dev/sda5  ext4             (not mounted)  3ff8f52b-26d0-415f-b890-9ed186c00c5b
/dev/sdb1  vfat             (not mounted)  A023-0678
/dev/sdb2  ext4             (not mounted)  fb4b6aab-3aa9-4f22-ac08-957d3765f525
/dev/sdb3  ntfs             (not mounted)  01D21F5BB33EFBA0
/dev/sdb4  ntfs    Win10    (not mounted)  7B637EED5EAE730B
/dev/sdb6  ext4             (not mounted)  649ff9fc-1a34-4427-9ca4-9310bff5963a
/dev/sdb7  swap             [SWAP]         db1e3a9e-cd9d-48de-8e42-e674b4fdb699
/dev/sdb8  ext4             (not mounted)  1c6d2b39-7de5-4e00-a7d4-7e237fb789f8
/dev/sr0   udf     DVDVIDEO /media/ubuntu/DVDVIDEO 2017-01-05-22-29-57-00
/dev/sdc1  ntfs    TOSHIBA  /media/ubuntu/TOSHIBA A46CE4BB6CE488FE
/dev/sdd1  iso9660 Ubuntu 16.04.1 LTS amd64 (in use) 2016-07-19-21-27-51-00
/dev/sdd2  vfat             (in use)       0F7B-9366


```


```


ubuntu@ubuntu:/media/ubuntu/649ff9fc-1a34-4427-9ca4-9310bff5963a/etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=649ff9fc-1a34-4427-9ca4-9310bff5963a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=A023-0678  /boot/efi       vfat    umask=0077      0       1

# /home was on /dev/sda8 during installation
UUID=1c6d2b39-7de5-4e00-a7d4-7e237fb789f8 /home           ext4    defaults        0       2

# swap was on /dev/sda7 during installation
UUID=db1e3a9e-cd9d-48de-8e42-e674b4fdb699 none            swap    sw              0       0
UUID=A023-0678    /boot/efi    vfat    defaults    0    1

#mountpoint for sda5 steam-files added 11Oct2016
UUID=3ff8f52b-26d0-415f-b890-9ed186c00c5b /mnt/steam-files            ext4    defaults        0       2

#mountpoint for sda5 steam-nelly added 23dec2106
UUID=3ff8f52b-26d0-415f-b890-9ed186c00c5b /mnt/steam-nelly            ext4    defaults        0       2

#mountpoint for sda3 partition_377 added 01Jan2017
UUID=1cc33a38-c617-4e9e-acf4-19c79415609e /mnt/partition_377            ext4    defaults        0       2

#mountpoint for sda2 315gb added 04Jan2017
UUID=90e8492c-c40d-44ea-a370-941cc17a6d2d /mnt/315gb            ext4    defaults        0       2



```

I hope this gives you enough to see what the situation is.
What should be my next step then?
As far as I know, it seems I'll be doing the work from a Live USB drive, you may want to keep this in mind as this will affect the command lines.

Thanks guys,

---

### Post by Geoffrey_Arndt on 2017-01-08
The best & safest way to have a separate /home is during the installation process.    

If /home is on an HDD versus SSD.    You may have marginally more room.   But the system will be MUCH slower.

Really, best scenario overall is to have a large 256 GiB or larger SSD, and then use a second internal or external drive for the DATA and for file space hoggers like media files (especially video).

So, there are other solutions . . . but i like to gravitate to the cleanest ones.

---

### Post by TheFu on 2017-01-09
javierdl - did everything work out?  Posting data without a question is confusing. Why was it posted? Sorry, if I missed something.  Over a few weeks, things tend to change. What's new on the system?  

Seems, 
a) You were trying to move HOME to a different disk and follow a guide.
b) You did this from a live-boot CD/Flash drive. Good. That was expected.
c) ????

---

### Post by javierdl on 2017-01-10
Hi TheFu,

When I did post #6, I was at work, hence I wasn't able to get the drives information. Reason why I had to leave that part for later. Then later, from home, I finally got this information and made post #7.
a) and b) are right.
Now, here's where I am at the moment:
```

ubuntu@ubuntu:/media/ubuntu/1c6d2b39-7de5-4e00-a7d4-7e237fb789f8$ ls
angelique  javier  lost+found  nelly

ubuntu@ubuntu:/media/ubuntu/1c6d2b39-7de5-4e00-a7d4-7e237fb789f8$ sudo chmod 750 angelique
ubuntu@ubuntu:/media/ubuntu/1c6d2b39-7de5-4e00-a7d4-7e237fb789f8$ sudo chmod 750 nelly
ubuntu@ubuntu:/media/ubuntu/1c6d2b39-7de5-4e00-a7d4-7e237fb789f8$ sudo chmod 750 javier
ubuntu@ubuntu:/media/ubuntu/1c6d2b39-7de5-4e00-a7d4-7e237fb789f8$ ls -ltotal 28
drwxr-x--- 26 root root  4096 Jan  7 03:55 angelique
drwxr-x--- 44 root root  4096 Jan  7 03:56 javier
drwx------  2 root root 16384 Dec 11 06:03 lost+found
drwxr-x--- 24 root root  4096 Jan  7 03:57 nelly


```

After I did the above, I rebooted into the SSD. I attempted to enter into my own account, but nothing has changed. It still just flashes when I enter my password, and kicks me back out.
I also thought maybe I could use my last Backups backup, but the Live USB Backups says it needs to install some software for it to run, but it won't install it. I do not recall the message.

So, what should I do?

JDL

---

### Post by TheFu on 2017-01-10
Normally, the userid needs write permissions to their HOME.  750 doesn't do that. Also, it is common to have the userid be the OWNER of their HOME.
And lastly, the location of the new storage should be mounted to an empty /home directory - not under /media/  That area is for automatically mounted temporary storage.

Looks like you should start with that step-by-step guide again and follow the directions.  If the HOME for each userid isn't placed into the location that /etc/password says, then logins won't work.  While it doesn't HAVE TO BE /home, that is normal and better for a home user to follow.  At work, we don't usually use /home for user-home directories, BTW.

From here, it appears all you've accomplished is creating 3 directories.  Are there files under each?

---

### Post by javierdl on 2017-01-10
Thanks for replying TF &#128512;
About this: "the userid needs write permissions to their HOME"
How to do that when I'm not running Ubuntu normally, but from the Live USB drive?

If 750 won't do it, then what will?

Those 3 directories were there already. Except I moved them to 315gb/home, and then I copied them back (when I realized that "mv" had not just copied them to the new location, but also removed them from the original location). 
Thanks again TF &#128512;

---

### Post by TheFu on 2017-01-10
mv = move. It moves things.  **man mv** explains that. Don't run commands that you don't understand.
To copy, use cp ... or rsync or whatever backup tool makes copies that you like.  If you'd have used **sudo cp -p**, then all the permissions would have come over unmolested. The same for **sudo rsync -avz**.  Live and learn.  Linux and Unix are multi-user OSes from the ground up.  File and directory permissions are the basis for 98% of all Unix security.

**chmod** has a hole list of permissions. A basic understanding of those is required to run any Unix/Linux system.  There are tutorials. Best to learn this sooner than later.  Spend 45 min playing around with a few different userids, groups, and temporary directories as you work through a tutorial.  

Owners on a file system are just uid/gids.  These are numbers.  Look up the numbers in the /etc/passwd file in the OS partition, not the live-boot OS.  The manpage for chmod explains how to set owner/group using numbers, not names for the userid/groupid.  I'm being specific here.  userid = thefu (letters). uid=1020 (a number). The same applies to groupid (letters) and gid (number).

I cannot tell you what to type. Sorry. It is different on your system than mine. I'd rather teach you how to fish than hand you a fish too.

Just think of how much you are learning through this effort!  Fun stuff!

---

### Post by Bashing-om on 2017-01-15
javierdl; Well ..

I am asked in PM to look into this matter and offer a bit of guidance . so
Here goes.

@javierdl; we establish a base line for resolution of the issue:
from a liveUSB mount the new /home and we have a looksee.
so in this live environment:
```

sudo mkdir /mnt/looksee
sudo mount /dev/sdb8 /mnt/looksee

```
Now show us what we are working with, post back:
```

ls -al /mnt/looksee

``` we get a bit of direction here and

To back out - we mounted, we must also UNmount :
```

sudo umount /dev/sdb8

```

[INDENT][INDENT]see where we can go and what needs to be done.

[INDENT][INDENT][INDENT]we can do that[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2017-01-16
First off, thank you ever so kindly for complying with my humble request :)

Here's the feedback:

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/looksee
ubuntu@ubuntu:~$ sudo mount /dev/sdb8 /mnt/looksee
ubuntu@ubuntu:~$ ls -al /mnt/looksee
total 32
drwxr-xr-x  6 root root  4096 Jan  7 03:57 .
drwxr-xr-x  1 root root    60 Jan 16 16:39 ..
drwxr-x--- 26 root root  4096 Jan  7 03:55 angelique
drwxr-x--- 44 root root  4096 Jan  7 03:56 javier
drwx------  2 root root 16384 Dec 11 06:03 lost+found
drwxr-x--- 24 root root  4096 Jan  7 03:57 nelly
ubuntu@ubuntu:~$ sudo umount /dev/sdb8
ubuntu@ubuntu:~$ 



```

---

### Post by Bashing-om on 2017-01-16
javierdl; Yukkie;

Not at all what I had anticipated to see.
I got to do some checking and verifying that what I expected is what should be,
In the meantime I want that you label your partitions so I "know" what I am looking at.
Not only do they display in terminal, they display as labeled in Ubuntu, which makes it a lot easier than perhaps displaying a UUID. 
Here is the command to label your partitions:
```

sudo tune2fs -L "xenial" /dev/sda3
sudo tune2fs -L "xhome" /dev/sdb8

```
As examples, swap partition is already labeled so not to re-do swap - please label all the other partitions. .
Make the identifier that is between the quote marks what ever you are comfortable with for a name .

Once the labels are applied, show me a new :
```

sudo parted -l
sudo fdisk -lu

```

I get caught up and do my homework and I get back to you .

[INDENT][INDENT]there is a way that seems right
[INDENT][INDENT][INDENT]but leads to a broken system[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2017-01-16
I think all he needs to do is set the userid:groupid for each user correctly, then mount the new partition to /home/  
Run that way for a day, see that everything works, the clean up the "hidden" original /home/{whatever} directories on the main disk.

for example ... ```

sudo chown -R nelly:nelly /mnt/looksee/nelly
```
Do the same for the other directories, just with the correct userid/groupid for each. This is one of those things that is harder to say/write than to do.

---

### Post by Bashing-om on 2017-01-16
@TheFu . Hey ole bud .


I am not seeing what I expect . As a directory for /home, and in this /home directory I would expect to see the sub-directories for the users angelique, javier, and nelly .

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
> 
 This works because /home has a subdirectory for each user's settings and files which contain all the data & settings of that user.

Can you, TheFu , confirm this as a valid data structure ? I think we have here a failure to properly copy the original /home directory .
And yeah also could be access and permission issues at play here . But one can not access what does not exist .


@javierdl;
Have you removed the original /home ? If the original is still in residence we can look and compare .

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]

---

### Post by javierdl on 2017-01-16
Hi BO, TF,

Here's what I got 

```


ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32           EF    boot, esp
 5      538MB   301GB   300GB   ext4
 2      301GB   615GB   315GB   ext4                  msftdata
 3      615GB   992GB   377GB   ext4
 4      992GB   1000GB  8523MB  linux-swap(v1)        diag


Model: ATA Patriot Torch LE (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  211MB   210MB   fat32                 boot, esp
 2      211MB   228MB   16.8MB  ext4            Mi    msftres
 3      228MB   1026MB  799MB   ntfs                  msftdata
 4      1026MB  88.6GB  87.6GB  ntfs                  msftdata
 6      88.6GB  109GB   20.8GB  ext4
 7      109GB   110GB   386MB   linux-swap(v1)
 8      110GB   120GB   10.3GB  ext4            sd8


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End     Size    Type     File system  Flags
 1      106MB  2000GB  2000GB  primary  ntfs


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? i                                                          
Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdd: 16.0GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1499MB  1501MB  2425kB               EFI


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: MATSHITA DVD-RAM SW840 (scsi)                                      
Disk /dev/sr0: 80.5MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1459982336 bytes, 2851528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1B1FA484-E02B-4FAA-906D-10D3D588B00B

Device          Start        End   Sectors   Size Type
/dev/sda1        2048    1050623   1048576   512M EFI System
/dev/sda2   586989568 1201389567 614400000   293G Microsoft basic data
/dev/sda3  1201389568 1936877567 735488000 350.7G Linux filesystem
/dev/sda4  1936877568 1953523711  16646144     8G Windows recovery environment
/dev/sda5     1050624  586989567 585938944 279.4G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A62FCAC7-9491-47C0-BE48-46384F1AD03B

Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    411647    409600   200M EFI System
/dev/sdb2     411648    444415     32768    16M Microsoft reserved
/dev/sdb3     444416   2004319   1559904 761.7M Microsoft basic data
/dev/sdb4    2004320 173001607 170997288  81.6G Microsoft basic data
/dev/sdb6  173002752 213577727  40574976  19.4G Linux filesystem
/dev/sdb7  213577728 214331391    753664   368M Linux swap
/dev/sdb8  214331392 234440703  20109312   9.6G Linux filesystem


Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x545e75e9

Device     Boot  Start        End    Sectors  Size Id Type
/dev/sdc1       206848 3907024064 3906817217  1.8T  7 HPFS/NTFS/exFAT


Disk /dev/sdd: 3.8 GiB, 4009754624 bytes, 7831552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x40a863e7

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdd1  *          0 2955679 2955680  1.4G  0 Empty
/dev/sdd2       2927216 2931951    4736  2.3M ef EFI (FAT-12/16/32)


```

> 

@javierdl;
Have you removed the original /home ? If the original is still in residence we can look and compare .


Well, that was my mistake precisely. I did remove the 3 account folders from "xhome" with "mv". Then I copied them back from the destination. So at the moment they are there. I hope this answers your question.

Back to you,

JDL

---

### Post by Bashing-om on 2017-01-16
javierdl; Well,

Let us look and see what it is that we have to work from, to copy back to the new home;
from the liveUSB:
```

sudo mount /dev/sdb6 /mnt/looksee
ls -al /mnt/looksee
ls -al /mnt/looksee/home

```

when done UNmount !
```

sudo umount /dev/sdb6

```


[INDENT][INDENT]maybe a tale gets told
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-01-16
MUCH easier and more convenient would have been to create a /data partition (named what you want) and to move the contents of /home directory to there and symlink to it from the now empty /home directory. This is done simply and easily in about 10-15 minutes. 

Using this method you can also aim the Windows data folder at /data (if the /data partition is NTFS) and both OSs can use the same data. No redundancy. Moving /home directory to a /home partition, Windows can't access the data (unless NTFS /home partition). 

Good luck.

---

### Post by TheFu on 2017-01-17
I don't have a clue what is going on here. Post #13 says to look in the passwd file to get the userid/groupids for the HOME directories. Haven't see that done.

I suspect the copy-back of the data after the move wasn't done correctly. Permissions were lost. With HOME directories, that isn't all that important. Changing the owner to be the correct userid ought to fix it completely.  Not much harm done, but every tiny issue can seem like a mountain to someone unfamiliar with what is actually needed.

For a userid to be able to login, the value of the HOME inside the /etc/passwd needs to match the actual location. /home/{userid} is normal, but not actually required.  For example, on some of my systems:
```
$ grep thefu /etc/passwd
thefu:x:1000:1000:T F:/export/home/thefu:/bin/bash
```

See the /export/home/thefu directory?  That is the location of the HOME for that userid.  Every userid can have a different partition for their HOME, if desired. This cmd shows the HOME:
```
$ ls -ld /export/home/thefu
drwxr-xr-x 160 thefu thefu 20480 Jan 17 06:41 /export/home/thefu/
```

See the userid:groupid (thefu:thefu) and permissions (755)?  Those permissions are what 99% of home directories need.

So ... there are multiple ways to make this happen for javierdl.  How it happens isn't important, just that the result ends up this way for each user.  The /etc/passwd --> HOME location for each user needs to be correct. Either the passwd file can be changed to point to the new location or the storage needs to be placed into the location specified in the passwd file. That is where mounting to the correct location via the fstab matters. Regardless, the owner, group, and permissions need to change as the example above shows.  The passwd file is just a text file in a specific format. use sudoedit /etc/passwd to modify it, if you like.  **Don't screw anything up or it will be bad.** Definitely make a backup of it before making any changes.

I don't know how to explain this any clearer in these forums.

P.S. - if network userid are being used, then use the normal LDAP access methods to get the record for any userid. Not all setups use the /etc/passwd file for normal userids.

---

### Post by javierdl on 2017-01-17
> **Bashing-om said:**
> javierdl; Well,

Let us look and see what it is that we have to work from, to copy back to the new home;
from the liveUSB:

[INDENT][INDENT]maybe a tale gets told
[/INDENT]
[/INDENT]


```


ubuntu@ubuntu:~$ **sudo mkdir /mnt/looksee**
ubuntu@ubuntu:~$ **sudo mount /dev/sdb6 /mnt/looksee**
ubuntu@ubuntu:~$ **ls -al /mnt/looksee**
total 144
drwxr-xr-x  26 root root  4096 Jan  7 01:35 .
drwxr-xr-x   1 root root    60 Jan 17 15:43 ..
drwxr-xr-x   2 root root  4096 Dec  3 03:17 5968-2E1F
drwxr-xr-x   2 root root  4096 Dec 17 16:17 bin
drwxr-xr-x   4 root root  4096 Jan  1 19:44 boot
drwxr-xr-x   2 root root  4096 Oct  6 03:28 cdrom
drwxr-xr-x   5 root root  4096 Jul 19 20:50 dev
drwxr-xr-x 148 root root 12288 Jan 11 23:56 etc
drwxr-xr-x   2 root root  4096 Oct  6 03:26 home
lrwxrwxrwx   1 root root    32 Dec 22 17:51 initrd.img -> boot/initrd.img-4.4.0-57-generic
lrwxrwxrwx   1 root root    32 Dec  8 16:23 initrd.img.old -> boot/initrd.img-4.4.0-53-generic
drwxr-xr-x  24 root root  4096 Dec 11 06:04 lib
drwxr-xr-x   2 root root  4096 Dec 11 06:04 lib32
drwxr-xr-x   2 root root  4096 Dec 11 06:04 lib64
drwx------   2 root root 16384 Oct  6 03:26 lost+found
drwxr-xr-x  10 root root  4096 Jan 11 23:56 media
drwxr-xr-x   6 root root  4096 Jan  2 16:34 mnt
drwxr-xr-x   4 root root  4096 Oct 30 04:09 opt
drwxr-xr-x   2 root root  4096 Apr 12  2016 proc
drwx------  10 root root  4096 Dec 11 06:03 root
drwxr-xr-x  12 root root  4096 Jul 19 20:52 run
drwxr-xr-x   2 root root 12288 Dec 31 04:29 sbin
drwxr-xr-x   2 root root  4096 Jun 29  2016 snap
drwxr-xr-x   2 root root  4096 Jul 19 20:42 srv
drwxr-xr-x   2 root root  4096 Feb  5  2016 sys
drwxrwxrwt   8 root root 20480 Jan 11 23:57 tmp
drwxr-xr-x  12 root root  4096 Oct  8 04:32 usr
drwxr-xr-x  14 root root  4096 Jul 19 20:54 var
lrwxrwxrwx   1 root root    29 Dec 22 17:51 vmlinuz -> boot/vmlinuz-4.4.0-57-generic
lrwxrwxrwx   1 root root    29 Dec  8 16:23 vmlinuz.old -> boot/vmlinuz-4.4.0-53-generic
ubuntu@ubuntu:~$ ls -al /mnt/looksee/home
total 8
drwxr-xr-x  2 root root 4096 Oct  6 03:26 .
drwxr-xr-x 26 root root 4096 Jan  7 01:35 ..
ubuntu@ubuntu:~$ **sudo umount /dev/sdb6**


```

---

### Post by TheFu on 2017-01-17
Well, that shows the original /home is empty. Ready for the new partition (with data) to be mounted - modify the fstab in sdb6 to do that.

Look up the userids and groups in the /dev/sdb6 ... etc/passwd and group file there. Then chown -R each of the HOME directories for the specific userid/groupid.

---

### Post by Bashing-om on 2017-01-17
javierdl; Yeik;

At this point I do not know what it will take to fix your install .
For reference this is what one should see for a listing :
> 
sysop@x1604:/$ ls -al /home
total 12
drwxr-xr-x  3 root  root  4096 Oct 16 22:47 .
drwxr-xr-x 25 root  root  4096 Jan 10 10:56 ..
drwxr-xr-x 28 sysop sysop 4096 Jan 17 13:14 sysop
sysop@x1604:/$

where I am "sysop" here .

To my mind we just do not have much left to work with .
Build a new home from scratch I do not even know where to start .

[INDENT][INDENT]one of those times
[INDENT][INDENT][INDENT]ignorance gets the better of me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2017-01-17
I'm pretty sure that my posts have covered what is needed. Just worry that javierdl isn't understanding me. My failure completely. Sorry.  2 min on the box and I'm sure it could be fixed.

---

### Post by Bashing-om on 2017-01-17
@TheFu :)

> ** said:**
> I'm pretty sure that my posts have covered what is needed. Just worry that javierdl isn't understanding me. My failure completely. Sorry.  2 min on the box and I'm sure it could be fixed.

Sure then that between the 3 of us we can work our way through . I am in this for the long haul - if that is what it takes .
I too am all for what I can learn in this experience.
@ javierdl;;
We follow TheFu's lead here, and I will continue to look over the shoulders.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by TheFu on 2017-01-17
Ok - do everything from the live-boot.

First we need to mount the new storage with all the HOME directories onto /home/.  To do it, we need to make an fstab line, which needs some information. 
Lets agree on the following going forward:
/dev/sdb6 = the OS where all settings need to exist.
/dev/sdb8 = the new storage for HOME ....
This seems odd to me, but lacking any other current data, that appears to be correct.  YOU should check this, since devices can change at every boot. I think the partition numbers (6, 8) are probably correct but the drive device (/dev/sdb) is probably different. 

Mount both of these to temporary locations, until /mnt. To do that, 
```
$ sudo mkdir /mnt/root /mnt/home
$ sudo mount /dev/sdb6 /mnt/root 
$ sudo mount/dev/sdb8 /mnt/home
```

Then we need to make the fstab in /mnt/root/etc/fstab mount the new HOMEs at boot. Please post the output from 2 cmds (please, please, please use code tags):
```
$ more  /mnt/root/etc/fstab 
```
and 
```
$ sudo blkid 
```

These will help let us make the line for the fstab that you need.

---

### Post by javierdl on 2017-01-17
Wow! You guys are unbelievable! You are AWESOME! :)
As soon as I get back home I'll work on your requests TF :)
I can't wait!

Btw, TheFu,

> [COLOR=#000000]I'm pretty sure that my posts have covered what is needed. Just worry that javierdl isn't understanding me. My failure completely. Sorry...
[/COLOR]I totally agree, you have been great and not given up, which I appreciate immensely. The problem is that, indeed, I'm not at a level where I can fill in the blanks. Hence I do need the actual command lines too ;) So, no apology is needed :)

---

### Post by javierdl on 2017-01-17
> **Bucky Ball said:**
> MUCH easier and more convenient would have been to create a /data partition (named what you want) and to move the contents of /home directory to there and symlink to it from the now empty /home directory. This is done simply and easily in about 10-15 minutes. 

Using this method you can also aim the Windows data folder at /data (if the /data partition is NTFS) and both OSs can use the same data. No redundancy. Moving /home directory to a /home partition, Windows can't access the data (unless NTFS /home partition). 

Good luck.

Thanks a bunch for this info BB, I love it! Got to look into it, once everything is running normal again though.

JDL

---

### Post by javierdl on 2017-01-18
Ok TF, here it is:

```


ubuntu@ubuntu:~$ more  /mnt/root/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=649ff9fc-1a34-4427-9ca4-9310bff5963a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=A023-0678  /boot/efi       vfat    umask=0077      0       1

# /home was on /dev/sda8 during installation
UUID=1c6d2b39-7de5-4e00-a7d4-7e237fb789f8 /home           ext4    defaults        0       2

# swap was on /dev/sda7 during installation
UUID=db1e3a9e-cd9d-48de-8e42-e674b4fdb699 none            swap    sw              0       0
UUID=A023-0678    /boot/efi    vfat    defaults    0    1

#mountpoint for sda5 steam-files added 11Oct2016
UUID=3ff8f52b-26d0-415f-b890-9ed186c00c5b /mnt/steam-files            ext4    defaults        0       2

#mountpoint for sda5 steam-nelly added 23dec2106
UUID=3ff8f52b-26d0-415f-b890-9ed186c00c5b /mnt/steam-nelly            ext4    defaults        0       2

#mountpoint for sda3 partition_377 added 01Jan2017 
UUID=1cc33a38-c617-4e9e-acf4-19c79415609e /mnt/partition_377            ext4    defaults        0       2

#mountpoint for sda2 315gb added 04Jan2017 
UUID=90e8492c-c40d-44ea-a370-941cc17a6d2d /mnt/315gb            ext4    defaults        0       2
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="D45B-1044" TYPE="vfat" PARTLABEL="EF" PARTUUID="17b3568b-cb60-4224-bacf-1e231c3d27bf"
/dev/sda2: LABEL="315gb" UUID="90e8492c-c40d-44ea-a370-941cc17a6d2d" TYPE="ext4" PARTUUID="6c6cbafd-ee18-4b34-addc-6ae03a809e29"
/dev/sda3:  LABEL="xenial" UUID="1cc33a38-c617-4e9e-acf4-19c79415609e" TYPE="ext4"  PARTUUID="cc6bf447-b7a9-4d57-b8bf-5567225c6c7f"
/dev/sda5: UUID="3ff8f52b-26d0-415f-b890-9ed186c00c5b" TYPE="ext4" PARTUUID="f3f1b269-3173-418b-91f7-5ce9148732b4"
/dev/sdb1: UUID="A023-0678" TYPE="vfat" PARTUUID="7112358f-49c8-4736-a5ba-f88e8c948000"
/dev/sdb2:  UUID="fb4b6aab-3aa9-4f22-ac08-957d3765f525" TYPE="ext4" PARTLABEL="Mi"  PARTUUID="08d8b457-7664-41aa-babf-b15f41344911"
/dev/sdb3: UUID="01D21F5BB33EFBA0" TYPE="ntfs" PARTUUID="a49b3001-be18-3bb8-d358-d371d69b62f8"
/dev/sdb4: LABEL="Win10" UUID="7B637EED5EAE730B" TYPE="ntfs" PARTUUID="eccc32b8-9cac-4745-a11f-245f10f1e78d"
/dev/sdb6: UUID="649ff9fc-1a34-4427-9ca4-9310bff5963a" TYPE="ext4" PARTUUID="e49cb72e-1825-45c8-b28b-5ba1af8ca101"
/dev/sdb8:  LABEL="xhome" UUID="1c6d2b39-7de5-4e00-a7d4-7e237fb789f8" TYPE="ext4"  PARTLABEL="sd8" PARTUUID="2ae475cd-7a85-4330-9ba8-684706e9215f"
/dev/sdc1: LABEL="TOSHIBA" UUID="A46CE4BB6CE488FE" TYPE="ntfs" PARTUUID="545e75e9-01"
/dev/loop0: TYPE="squashfs"
/dev/sda4: UUID="e863d0f6-0ab2-4f1f-9fa3-55a652b02283" TYPE="swap" PARTUUID="2b80ca11-a894-49ae-a578-fcf41cb5b1e4"
/dev/sdb7: UUID="db1e3a9e-cd9d-48de-8e42-e674b4fdb699" TYPE="swap" PARTUUID="e93886f8-0dc8-484b-87c4-5b2f33f851a1"
/dev/sdd1:  UUID="2016-07-19-21-27-51-00" LABEL="Ubuntu 16.04.1 LTS amd64"  TYPE="iso9660" PTUUID="40a863e7" PTTYPE="dos" PARTUUID="40a863e7-01"
/dev/sdd2: SEC_TYPE="msdos" UUID="0F7B-9366" TYPE="vfat" PARTUUID="40a863e7-02"




```

---

### Post by TheFu on 2017-01-18
Thanks. Forgot to ask for a **df -h** - please.  That's the only way I'll know which UUIDs go with which data/mounts.  Sorry for the delay.

---

### Post by Bucky Ball on 2017-01-18
Bit off-topic, but noticed something immediately on looking at your output.

```
/dev/sda4: UUID="e863d0f6-0ab2-4f1f-9fa3-55a652b02283" TYPE="swap" PARTUUID="2b80ca11-a894-49ae-a578-fcf41cb5b1e4"
/dev/sdb7: UUID="db1e3a9e-cd9d-48de-8e42-e674b4fdb699" TYPE="swap" PARTUUID="e93886f8-0dc8-484b-87c4-5b2f33f851a1"
```

FYI: You don't need two swap partitions. You only *ever* need one and point all installs to it. The process of working out your current issue will probably demonstrate that is enough to do. You note the UUID of the /swap you want to use and make sure that is the /swap your fstab file is pointing to on boot. If it's not, then change the UUID so it is. Once that's done and you know both OSs are using the same /swap (by booting them and checking) then you can delete the redundant /swap. 

No point in having two /swaps (or two /home partitions for that matter). They both can't be used at the same time (you only boot one OS at once and that uses the ONE /swap) and having two can actually cause confusion somewhere down the track.

---

### Post by javierdl on 2017-01-18
Ok, I re-did the previous commands along with "df -h" now:

```


ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt/root
ubuntu@ubuntu:~$ sudo mount /dev/sdb8 /mnt/home
ubuntu@ubuntu:~$ **more /mnt/root/etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=649ff9fc-1a34-4427-9ca4-9310bff5963a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=A023-0678  /boot/efi       vfat    umask=0077      0       1

# /home was on /dev/sda8 during installation
UUID=1c6d2b39-7de5-4e00-a7d4-7e237fb789f8 /home           ext4    defaults        0       2

# swap was on /dev/sda7 during installation
UUID=db1e3a9e-cd9d-48de-8e42-e674b4fdb699 none            swap    sw              0       0

...skipping 1 line

#mountpoint for sda5 steam-files added 11Oct2016
UUID=3ff8f52b-26d0-415f-b890-9ed186c00c5b /mnt/steam-files            ext4    defaults        0       2

#mountpoint for sda5 steam-nelly added 23dec2106
UUID=3ff8f52b-26d0-415f-b890-9ed186c00c5b /mnt/steam-nelly            ext4    defaults        0       2

#mountpoint for sda3 xenial added 01Jan2017 
UUID=1cc33a38-c617-4e9e-acf4-19c79415609e /mnt/xenial            ext4    defaults        0       2

#mountpoint for sda2 315gb added 04Jan2017 
UUID=90e8492c-c40d-44ea-a370-941cc17a6d2d /mnt/315gb            ext4    defaults        0       2


ubuntu@ubuntu:~$ **df -h**
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.7M  1.6G   1% /run
/dev/sdd        1.5G  1.5G     0 100% /cdrom
/dev/loop0      1.4G  1.4G     0 100% /rofs
/cow            7.9G   45M  7.8G   1% /
tmpfs           7.9G  180K  7.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs           7.9G  4.0K  7.9G   1% /tmp
tmpfs           1.6G   76K  1.6G   1% /run/user/999
/dev/sdc1       1.9T  1.2T  663G  65% /media/ubuntu/TOSHIBA
/dev/sda3       346G  155G  174G  48% /media/ubuntu/xenial
/dev/sdb8       9.4G  8.3G  541M  95% /mnt/home
/dev/sdb6        19G  9.5G  8.5G  53% /mnt/root
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="D45B-1044" TYPE="vfat" PARTLABEL="EF" PARTUUID="17b3568b-cb60-4224-bacf-1e231c3d27bf"
/dev/sda2: LABEL="315gb" UUID="90e8492c-c40d-44ea-a370-941cc17a6d2d" TYPE="ext4" PARTUUID="6c6cbafd-ee18-4b34-addc-6ae03a809e29"
/dev/sda3: LABEL="xenial" UUID="1cc33a38-c617-4e9e-acf4-19c79415609e" TYPE="ext4" PARTUUID="cc6bf447-b7a9-4d57-b8bf-5567225c6c7f"
/dev/sda5: UUID="3ff8f52b-26d0-415f-b890-9ed186c00c5b" TYPE="ext4" PARTUUID="f3f1b269-3173-418b-91f7-5ce9148732b4"
/dev/sdb1: UUID="A023-0678" TYPE="vfat" PARTUUID="7112358f-49c8-4736-a5ba-f88e8c948000"
/dev/sdb2: UUID="fb4b6aab-3aa9-4f22-ac08-957d3765f525" TYPE="ext4" PARTLABEL="Mi" PARTUUID="08d8b457-7664-41aa-babf-b15f41344911"
/dev/sdb3: UUID="01D21F5BB33EFBA0" TYPE="ntfs" PARTUUID="a49b3001-be18-3bb8-d358-d371d69b62f8"
/dev/sdb4: LABEL="Win10" UUID="7B637EED5EAE730B" TYPE="ntfs" PARTUUID="eccc32b8-9cac-4745-a11f-245f10f1e78d"
/dev/sdb6: UUID="649ff9fc-1a34-4427-9ca4-9310bff5963a" TYPE="ext4" PARTUUID="e49cb72e-1825-45c8-b28b-5ba1af8ca101"
/dev/sdb8: LABEL="xhome" UUID="1c6d2b39-7de5-4e00-a7d4-7e237fb789f8" TYPE="ext4" PARTLABEL="sd8" PARTUUID="2ae475cd-7a85-4330-9ba8-684706e9215f"
/dev/sdc1: LABEL="TOSHIBA" UUID="A46CE4BB6CE488FE" TYPE="ntfs" PARTUUID="545e75e9-01"
/dev/loop0: TYPE="squashfs"
/dev/sda4: UUID="e863d0f6-0ab2-4f1f-9fa3-55a652b02283" TYPE="swap" PARTUUID="2b80ca11-a894-49ae-a578-fcf41cb5b1e4"
/dev/sdb7: UUID="db1e3a9e-cd9d-48de-8e42-e674b4fdb699" TYPE="swap" PARTUUID="e93886f8-0dc8-484b-87c4-5b2f33f851a1"
/dev/sdd1: UUID="2016-07-19-21-27-51-00" LABEL="Ubuntu 16.04.1 LTS amd64" TYPE="iso9660" PTUUID="40a863e7" PTTYPE="dos" PARTUUID="40a863e7-01"
/dev/sdd2: SEC_TYPE="msdos" UUID="0F7B-9366" TYPE="vfat" PARTUUID="40a863e7-02"


```

**Btw, I suppose I should now be unmounting sdb6 and sdb8, right?**
I hope this helps TF. 

BB, that's a very good point. In case that could get in the way of our present progress, shouldn't we take care of this asap? And remove one of the SWAPS ?

Btw, previously, we labeled sda3 "Xenial". Does this mean that all the OS files are supposed to be here in sda3? Because they are actually not here. They are at sdb6.

---

### Post by Bucky Ball on 2017-01-18
Disregard my comments about the /swap. My mistake. Just noticed they are on separate disks, anyhoo, so not an issue.
```

/dev/sda4: UUID="e863d0f6-0ab2-4f1f-9fa3-55a652b02283" TYPE="swap" PARTUUID="2b80ca11-a894-49ae-a578-fcf41cb5b1e4"
/dev/sdb7: UUID="db1e3a9e-cd9d-48de-8e42-e674b4fdb699" TYPE="swap" PARTUUID="e93886f8-0dc8-484b-87c4-5b2f33f851a1"
```

See? One's on sda and the other's on sdb. Doh! Shouldn't post when I've just gotten out of bed! ;)

---

### Post by TheFu on 2017-01-19
Thanks.

All of the depends on the fact that YOU WANT the partitions mounted to /mnt/root and /mnt/home to be the OS and the /home.  If not, this won't help and may be bad.  Looking now ... 

Ok - the fstab already in /mnt/root/etc/fstab is correct.  It is mounting the root and /home correctly.  That just leaves the userid:groupid ownership issue. There are a few different ways to accomplish this. We have to do it the harder way here, due to forum rules against allowing root to login directly.

To gather the needed info, please run and post:
```
$ egrep 'angelique|javier|nelly' /mnt/root/etc/passwd /mnt/root/etc/group
```
It is only the primary groups (actually the gids) that we need.
The next step is the chown using uids (not userid) on each of the home directories as needed. Something like:```

sudo chown -R 1000:1000 /mnt/home/javier
```, but we can't be sure without seeing the actual values. Wouldn't want to make assumptions that aren't correct.

And the others are probable 1001:1001 and 1002:1002, but might not be.  Which is which (including ~/javier) isn't known.

---

### Post by javierdl on 2017-01-20
```

ubuntu@ubuntu:~$ egrep 'angelique|javier|nelly' /mnt/root/etc/passwd /mnt/root/etc/group
grep: /mnt/root/etc/passwd: No such file or directory
grep: /mnt/root/etc/group: No such file or directory


```

---

### Post by TheFu on 2017-01-20
Appears that /mnt/root/ is NOT the OS you want to use.  You will need to find that and work through this again. Assuming /mnt/root has the partition mounted.  Those are base assumptions that must be resolved.  See post #28 - the assumptions made there need to be validated by you and all work done needs to be redone with the correct answers.

---

### Post by javierdl on 2017-01-20
How is this?

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/root /mnt/home
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt/root
ubuntu@ubuntu:~$ sudo mount /dev/sdb8 /mnt/home
ubuntu@ubuntu:~$ egrep 'angelique|javier|nelly' /mnt/root/etc/passwd /mnt/root/etc/group
/mnt/root/etc/passwd:javier:x:1000:1000:Javier Diaz de Leon,,,:/home/javier:/bin/bash
/mnt/root/etc/passwd:angelique:x:1001:1001:angelique,,,:/home/angelique:/bin/bash
/mnt/root/etc/passwd:nelly:x:1002:1002:Nelly,,,:/home/nelly:/bin/bash
/mnt/root/etc/group:adm:x:4:syslog,javier
/mnt/root/etc/group:cdrom:x:24:javier
/mnt/root/etc/group:sudo:x:27:javier,nelly
/mnt/root/etc/group:dip:x:30:javier
/mnt/root/etc/group:plugdev:x:46:javier
/mnt/root/etc/group:lpadmin:x:113:javier
/mnt/root/etc/group:nopasswdlogin:x:115:angelique
/mnt/root/etc/group:javier:x:1000:
/mnt/root/etc/group:sambashare:x:128:javier
/mnt/root/etc/group:angelique:x:1001:
/mnt/root/etc/group:nelly:x:1002:nelly
/mnt/root/etc/group:3ofus:x:1003:javier,nelly,angelique




```

---

### Post by TheFu on 2017-01-20
So you just need to chown for each HOME to match those uid:gid for each of the users.  Got it? See example above.

That should be the end. Reboot into the real OS after that is done.

---

### Post by javierdl on 2017-01-20
[SIZE=5]**A milestone reached!!!!**[/SIZE]
I'm back in!!!
Thanks a million TheFu :) and Bucky Ball, Bashing-om, and Geoffrey Arndt.

Now the only problem is that I am getting many errors from attempts to update software (see attached images).

Do you think I should prepare to reinstall Ubuntu, might as well? 
Or can this be easily fixed?

Also, it seems I need a larger partition for Home after all: I am getting a "Low Disk Space" popup message.

---

### Post by Bucky Ball on 2017-01-20
This is definitely the stuff of another thread as it has nothing to do with your original support request. If your original issue is fixed you should mark this thread as solved and best to start another as you do your chances of support no favours by posting about a new issue five pages deep on a thread about a something else. 

In the meantime, try installing 'ubuntu-restricted-extras' to fix the ttf-mscorefonts-installer issue. Tell us what happens in a new thread and post a link to that here if you like. Good luck. ;)

PS: Just read your last line. If you have good backups and nothing to lose, yes, why not a reinstall and make it clean. Get out that paper and pen and make a decent plan of what you want the end result to look like and go for it. Again, any issues reinstalling should be in 'Installations and Upgrades', not tacked on to this thread. ;)

PPS: Also best to attach pics. Go Advanced or Adv Reply and the paperclip icon.

---

### Post by javierdl on 2017-01-20
BB, fair enough, I like your idea :)
Yes, good thing is I do have backups. So I'll just reinstall Ubuntu. 
One thing is for sure: I'll make a larger partition JUST for home ;)
I guess I'll skip installing the [COLOR=#000000]ubuntu-restricted-extras.

I went into the Edit mode for my previous post, but I didn't see the Attach paperclip icon :([/COLOR]

---

### Post by Bucky Ball on 2017-01-21
You hit 'Edit Post' then 'Go Advanced' and you'll find the paperclip there in the toolbar at the top of the text box. ;)

Good luck. ;)

---

### Post by TheFu on 2017-02-07
Thought I'd add a command should anyone just want to change the HOME for a userid. This assumes the storage stuff is already available.
```
sudo usermod -d /var/joe -m joe
```
Will create the /var/joe, move all the files from wherever ~joe is (based on the current passwd DB), and modify the current passwd DB for joe to point to the new location.  Can be handy.  I was shocked at how quick and easy this was .... it moves the files, so the time it takes may not be quick.  Don't do this when the "joe" user is logged in.
Could be some other details that are important across the different releases, so be certain to check the manpage carefully.

---

