---
title: "Mounting external USB drive"
date: 2006-11-21
forum: General Help
---

### Post by jimmymac on 2006-11-21
Hi guys,

I'm trying to get an external USB drive to mount automaticallly into the specified mount point. 
It works fine if I mount manually but not auto from boot.
Anyway here's the fstab line I've put in:

/dev/sda2       /files          ext3    defaults,auto   0       0


Cheers,

Jimmy

---

### Post by taurus on 2006-11-21
Try to edit your /etc/fstab and modify that line to look like this!

```
/dev/sda2 /files ext3 defaults 0 2
```

---

### Post by jimmymac on 2006-11-21
Ok I did that and it seemed to work, however....

Two questions,

1.  What did I just do?!

2.  I now get the error message:

The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
       e2fsck -b 8193 <device>

What does this mean?  Does it have anything to do with the fact that it's ext3 not ext2?

MTIA

Cheers,

Jimmy

---

### Post by taurus on 2006-11-21
Are you sure it's ext3?  What is the output of this command from a terminal then?

```
sudo fdisk -l
```

---

### Post by jimmymac on 2006-11-21
You know I love this forum, fast and knowledgable replies...

Anyway...


Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        1340      996030   82  Linux swap / Solaris

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       36481   293033601   83  Linux


Cheers,

Jimmy

---

### Post by taurus on 2006-11-21
Do you currently have anything on /dev/sda2?  You can always reformat it to ext3 if you want.  Also, what does it look like when you run this command?

```
ls -la /files
```

---

### Post by jimmymac on 2006-11-21
Yeah there's a fair old bit of stuff on there...

total 7688
drwxr-xr-x  23 user root    4096 2006-11-20 21:04 .
drwxr-xr-x  22 root root    4096 2006-11-20 19:05 ..
-rw-r--r--   1 user root 7987200 2005-12-09 21:57 default.xbe
drwxr-xr-x   7 user user    4096 2006-06-05 23:26 Film
drwxr-xr-x   4 user root    4096 2006-10-19 17:03 Flashutils
drwxr-xr-x  10 user user    4096 2006-09-09 21:48 Games
drwxr-xr-x   2 user user    4096 2006-07-23 12:44 Images
drwxr-xr-x   4 user user    4096 2006-09-08 20:54 Linux Backup
drwxr-xr-x   4 user user    4096 2006-09-08 20:54 Linux Utilities
drwx------   2 root root   16384 2006-09-09 18:04 lost+found
drwxr-xr-x   4 user user    4096 2006-03-01 20:03 Manuals
drwxr-xr-x 414 user user   12288 2006-11-20 21:15 Music
drwxr-xr-x  30 user user    4096 2006-09-23 22:32 My Documents
drwxr-xr-x   2 user root    4096 2006-09-10 21:44 nx9105_xp_drivers
drwxr-xr-x  28 user user    4096 2006-03-01 20:10 Pictures
drwxr-xr-x   4 user user    4096 2006-09-08 20:56 Programs
drwxr-xr-x   3 user root    4096 2006-10-23 23:39 Recycled
drwxr-xr-x   4 user root    4096 2006-09-10 21:51 tbffbackup
drwx------   3 user user    4096 2006-09-13 18:19 .Trash-james
drwxr-xr-x   2 user user    4096 2006-11-20 12:10 Ubuntu
drwxr-xr-x   3 user user    4096 2006-10-22 21:00 Utilities

Going on what you just said, does that mean it's ext2?

Cheers,

Jimmy

---

### Post by jimmymac on 2006-11-21
Maybe I should mention that originally it was an NTFS (god forbid) drive.
I shrunk the partition and formatted the rest of it as (what I thought was) ext3 in partition magic, and copyed over.  Then extended the new partition to fill the drive...

Cheers,

Jimmy

---

### Post by taurus on 2006-11-21
Are you the user "user" on that machine?  Can you create or delete anything in /files _without_ using the sudo command?

---

### Post by jimmymac on 2006-11-22
Yes I'm 'user'.  I have no problems making, deleting etc.

user@venus:/files$ mkdir test
user@venus:/files$ ls
360Share     Linux Backup     nx9105_xp_drivers  Ubuntu
default.xbe  Linux Utilities  Pictures           Utilities
Film         lost+found       Programs           XBox
Flashutils   Manuals          Recycled           XboxMediaCenter.xml
Games        Music            tbffbackup         XBox XBMC
Images       My Documents     test
user@venus:/files$


Cheers,

Jimmy

---

