---
title: "Gparted questions"
date: 2007-10-01
forum: General Help
---

### Post by olliecampbell on 2007-10-01
Hi,

A few more gparted questions im afraid...I have searched! Promise!

Ive got a triple boot Ubuntu install on my Macbook Pro at the moment and have 40gb of unused space on the drive. I'd like to format this as a spare partition to dump files onto so that each OS can see them, say FAT32.

I started up gparted and got an error straight away:
> 
Unable to mount the volume.
[mntent]: line 8 in /etc/fstab is bad
mount: can't find /media/Untitled in /etc/fstab or /etc/mtab

Ive attached a screenshot of Gparted and how it looks after it loads as well as the contents of my fstab below.



> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=15fd684d-5acb-4517-a290-01a8ab91a3ed /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=1A3080C43080A7F9 /media/Untitled 3       ntfs            defaults,nls=utf8,umask=007,gid=46 0 1
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
/swapfile       swap    swap    defaults        0       0



As you can tell im a newb at this, so any help would be appreciated. I would like to try and merge the 40gb partition with the 900mb partition and format it all as FAT32....please

Thanks in advance. :)

---

### Post by ThrobbingBrain66 on 2007-10-01
The UUID for /media/Untitled looks suspect (only 16 digits).  All my UUIDs are 32 digits long.

Also, I don't think merging the two unallocated spaces will work with the ntfs partition inbetween them. 

Sorry I can't be of more help, partitioning isn't my strong-suit.

---

### Post by qpieus on 2007-10-01
When you boot your pc, is the /media/Untitled directory mounted properly? Or is it only gparted that thinks the partition is not mounted.

The```
/media/Untitled 3 ntfs
```
part of line 8 looks fishy. What's that 3 doing there? Here's an example of an ntfs partition fstab line I found with a search
```
/dev/hdb1 /mnt/windows ntfs ro,umask=0222 0 0
```
So, it looks like that 3 in your line 8 shouldn't be there.
Was your mount point supposed to be /media/Untitled<space>8  by chance? If so, I think fstab lines can't have spaces in the mount point.

---

### Post by dcstar on 2007-10-02
> **olliecampbell said:**
> Hi,

A few more gparted questions im afraid...I have searched! Promise!

Ive got a triple boot Ubuntu install on my Macbook Pro at the moment and have 40gb of unused space on the drive. I'd like to format this as a spare partition to dump files onto so that each OS can see them, say FAT32.

I started up gparted and got an error straight away:
.........
Thanks in advance. :)

```
UUID=1A3080C43080A7F9 /media/**Untitled 3** ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```

Should probably be:

```
UUID=1A3080C43080A7F9 /media/**Untitled_3** ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```

The space between "Untitled" and "3" should not be there!

Manually edit your /etc/fstab file with:

```
gksudo gedit /etc/fstab
```

---

### Post by olliecampbell on 2007-10-04
Ahh I think i remember creating the partitions and they being named Untitled, Untitled 2, Untitled 3..with the spaces....could be where the problem comes from!


Tried the gparted live CD, but cant get X to start on it!

---

### Post by qpieus on 2007-10-05
Follow dcstar's advice and change the line in fstab to read

UUID=1A3080C43080A7F9 /media/Untitled_3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

After you remove that space, it should mount properly.

Don't know about gparted live not able to start x. Have you used the gparted  livecd before?

---

### Post by olliecampbell on 2007-10-06
> **qpieus said:**
> Follow dcstar's advice and change the line in fstab to read

UUID=1A3080C43080A7F9 /media/Untitled_3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

After you remove that space, it should mount properly.

Don't know about gparted live not able to start x. Have you used the gparted  livecd before?

Ok, so Ive replaced the space with an underscore, less error messages in gparted now, but it wont create a new extended partiton. I get an error saying something along the lines of :

"GPT doesnt support extended partitions"


Ive not used the gparted livecd before.

---

### Post by qpieus on 2007-10-08
What are the error messages gparted is now giving you? Also, when you boot into ubuntu, do your partitions mount OK?

---

