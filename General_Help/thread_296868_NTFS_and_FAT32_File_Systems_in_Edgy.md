---
title: "NTFS and FAT32 File Systems in Edgy"
date: 2006-11-10
forum: General Help
---

### Post by EmyrB on 2006-11-10
Hi all (yes its me, the question man again)

I have a system that is a dual boot machine (Windows XP and Edgy).
During the install, I selected the Windows drive that I need to have access to when in Edgy (/media/hda2), as it is 50GB Windows XP can only format it NTFS.

So, as it will contain data that I need to be able to alter, writing to NTFS is still a bit hit and miss with NTFS-3G, the only alternative is FAT32 (as I still need to access the same partition through windows).

If I use GParted to delete the 50GB partition and then recreate it and format it with FAT32, I should then be able to write to it.

Will this new drive have the same UUID as the entry for the NTFS in fstab or will the repartitioning and format change it?

Also, how would I then go about changing the entry in fstab for the FAT32 formated partition?

---

### Post by givré on 2006-11-10
> **EmyrB said:**
> Hi all (yes its me, the question man again)

I have a system that is a dual boot machine (Windows XP and Edgy).
During the install, I selected the Windows drive that I need to have access to when in Edgy (/media/hda2), as it is 50GB Windows XP can only format it NTFS.

So, as it will contain data that I need to be able to alter, writing to NTFS is still a bit hit and miss with NTFS-3G, 
Hum, where did you see that, it's not really true. It's still beta, but r/w support is quite stable. [www.ntfs-3g.org](www.ntfs-3g.org)

> **EmyrB said:**
> If I use GParted to delete the 50GB partition and then recreate it and format it with FAT32, I should then be able to write to it.
Of course, if you set it correctly in fstab

> **EmyrB said:**
> Will this new drive have the same UUID as the entry for the NTFS in fstab or will the repartitioning and format change it?
For sure it will not be the same.
To know it, simply use :```

sudo vol_id -u /dev/hd*
```
But you can also still use /dev/hd* as the partition name in fstab.
> **EmyrB said:**
> Also, how would I then go about changing the entry in fstab for the FAT32 formated partition?
The more common doc use in this forum :
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by EmyrB on 2006-11-10
Thanks givré,

> Hum, where did you see that, it's not really true. It's still beta, but r/w support is quite stable. [www.ntfs-3g.org](www.ntfs-3g.org)

Never got this to work 100%, but I am willing to try again as this would be the easiest option as I wouldn't have to copy everything off the drive, then bin the partition, boot into Ubuntu, run GParted and recreate the partition, format it FAT32, then run the gauntlet with fstab.

Any good guides on this?

Cheers

EmyrB:-D

---

### Post by givré on 2006-11-10
The ntfs-3g driver is in universe.
For configuration, there is plenty of documentation.
You can have a look at the manual (man ntfs-3g)
You can also look at the usage section of the main page at [www.ntfs-3g.org](www.ntfs-3g.org)
To finish, you can also have a look at my howto : 
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by EmyrB on 2006-11-10
Ok, followed your guide and now the partition in question doesn't get mounted. Which was the problem I had before with ntfs-g3. Just so you know I am using the amd64 version of ubuntu edgy.

---

### Post by EmyrB on 2006-11-10
Also, here is my fstab file: -

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=c4bd10d3-54a7-4daf-bb94-3b5356af2545 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb4
UUID=e7d83be6-4899-423c-8d6c-78d24c5ea80e /home           ext3    defaults        0       2
# /dev/hda2
UUID=30D41A44D41A0D2A /media/hda2     ntfs-g3    defaults,locale=en_GB.utf8  0       0
# /dev/hda5
UUID=48D02CB1D02CA762 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=6EC0323DC0320BB9 /media/hda6     ntfs-g3    defaults,locale=en_GB.utf8  0       0
# /dev/hdb3
UUID=cc56255f-f41b-422f-aff5-54f504346d3a /usr            ext3    defaults        0       2
# /dev/hdb1
UUID=262b152c-1ae3-4b21-a67b-de128075e1e5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by EmyrB on 2006-11-10
Ok, I thought I had spotted the problem, instead of ntfs-3g I had put them as ntfs-g3 in my fstab. I corrected my mistake and still the partitions wont mount.

So it's back to my original plan and make the hda2 a 50GB FAT32 partition and mount it through fstab but with vfat as it's file type :(

---

### Post by givré on 2006-11-10
What give you :
```
sudo mount /media/hda6
```

But do what you want.

---

### Post by EmyrB on 2006-11-10
I did a n**tfs-3g /dev/hda2 /media/hda2** through a terminal as root and it mounted the partition and I could write to it.

The problems seems to be with fstab I think.

I shall reboot again and issue the mount command and see if that does the trick.

---

### Post by EmyrB on 2006-11-10
Ok, I issued sudo mount /media/hda2 after a reboot and it worked. It mounted my ntfs partition. So why is fstab not mounting the drives?

---

### Post by dannyboy79 on 2006-11-10
isn't another option with dual boot systems is to use the ext3 driver in winbloz? this way you don't have to have a special partition so that ubuntu and winbloz can share files. check it out here, [http://techpatterns.com/forums/about686.html](http://techpatterns.com/forums/about686.html)

---

### Post by givré on 2006-11-10
dannyboy79 is right, this is an other option that could be not worse the look at.

For your fstab problem, didn't look enough at it, it seems that you replace ntfs-**3g** by ntfs-**g3**.
The driver name is ntfs-3g for third generation NTFS driver
Just change that and that should works.

---

### Post by EmyrB on 2006-11-11
From my previous post: -

> Ok, I thought I had spotted the problem, instead of ntfs-3g I had put them as ntfs-g3 in my fstab. I corrected my mistake and still the partitions wont mount.

So I still seem to have a problem. Fstab doesn't mount my drives with ntfs-3g as the file system. If I change the entries in fstab back to ntfs they mount.

I shall give the ext3 file system a try through windows, it is an interesting concept that windows will be able to read a better file system like ext3 :)

I still would like to solve this, as the machine in question belongs to a friend of mine and he really like the idea of Linux and especially Ubuntu, so getting Ubuntu to read and write to a NTFS partition would be great.

Cheers

---

### Post by Jongi on 2006-11-11
In FC5, I use **ntfs-3g          silent,umask=0,locale=en_US.utf8**. Haven't setup ntfs-3g in Kubuntu Edgy yet.

---

### Post by EmyrB on 2006-11-11
I had a look at ext2ifs, but that will mean I transfer the not able to write issue from linux to windows. I need to be able to reand and write to the partition in question from both OS's.

---

### Post by EmyrB on 2006-11-11
Ok, this is beginning to bug me now.

Here is my fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=c4bd10d3-54a7-4daf-bb94-3b5356af2545 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb4
UUID=e7d83be6-4899-423c-8d6c-78d24c5ea80e /home           ext3    defaults        0       2
# /dev/hda2
UUID=30D41A44D41A0D2A /media/hda2     ntfs-3g silent,umask=0,locale=en_GB.utf8   0       0
# /dev/hda5
UUID=48D02CB1D02CA762 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=6EC0323DC0320BB9 /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=cc56255f-f41b-422f-aff5-54f504346d3a /usr            ext3    defaults        0       2
# /dev/hdb1
UUID=262b152c-1ae3-4b21-a67b-de128075e1e5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

When I boot up, there is no icon for hda2 on the desktop. But if I open a terminal and type

```
sudo mount -a
```

The partition mounts in /media/hda2 and it is writable:???: 

I have read somewhere that the file I should rename fstab.pre-uuid to fstab and be editing that file, but fstab.pre-uuid is empty.

Why can't I mount any ntfs-3g partitions through fstab, but I can mount ntfs partitions ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by szaka on 2006-11-11
Move the ntfs-3g line to the end in /etc/fstab. The /usr partition must be mounted before any ntfs-3g partitions.

---

### Post by Jongi on 2006-11-11
In Edgy using **ntfs-3g     defaults,locale=en_US.utf8   0    0** in fstab and its mounting

---

### Post by EmyrB on 2006-11-12
Hey szaka, Jongi, givré & dannyboy79

I did it. I am currently looking at my music folder on the desktop and it is possible to write to it :)

It was szaka's post that did it. I pasted the entry for /media/hda2 after /usr and it worked:D 

Many thanks to each of you for your patience and knowledge. I can now finish setting up Ubuntu on my friend's PC. Now, how do I get World of Warcraft to work....:-k 

Many thanks guys

EmyrB

---

