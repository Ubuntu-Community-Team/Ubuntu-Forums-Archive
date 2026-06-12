---
title: "Mounting and writing/reading FAT32"
date: 2006-11-30
forum: General Help
---

### Post by PrinceArithon on 2006-11-30
OK, I'm having a bit of a hard time here getting a FAT32 partition to mount

when I type in sudo fdisk -l this is my read out

/dev/sda1   *           1        3218    25848553+   7  HPFS/NTFS
/dev/sda2            3219        7272    32563755    f  W95 Ext'd (LBA)
/dev/sda3            7273       12161    39270892+  83  Linux
/dev/sda5            3219        5131    15366141    b  W95 FAT32
/dev/sda6            5132        7061    15502693+   7  HPFS/NTFS
/dev/sda7            7062        7272     1694826   82  Linux swap / Solaris

Can anyone help me out with this??

---

### Post by taurus on 2006-11-30
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by PrinceArithon on 2006-11-30
OK I first posted back that I had some problems.  I had some problems with being able to delete things from my 2 partitions that I'M looking at.  I have an ntfs and a fat32 partition.

Now it goes like this.  I couldn't delete anything from the ntfs partition, but I fixed that, when I did my fat32 partition went away, and now when I try to mount it it tells me it's already mounted, but I can't see it, and I have unmounted it and then mounted it

Is there something I'm doing wrong??

This is my output:

sudo mount /fat_files
mount: /dev/sda5 already mounted or /fat_files busy
mount: according to mtab, /dev/sda5 is already mounted on /fat_files

Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3 -- converted during upgrade to edgy
UUID=dfab9928-7e46-4123-82ac-ba01c06c3968 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=3e4d8662-2dd4-4b03-9ec3-5ec47449209a none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1   /media/windows    ntfs-3g    defaults,locale=en_US.utf8,umask=0222   0    0
/dev/sda5    /fat_files vfat  iocharset=utf8,umask=000  0    0

What should I change??

---

### Post by PrinceArithon on 2006-11-30
Well I have to update a bit more on the problem.  I have found the FAT32 partition.  The thing is I found it under my system monitor.  I can open it and write to it.  I haven't went to windows yet to find out if I can read it and write to it as well.  The thing is I can't find it anywhere else...and I deffinatly am not getting an icon on my desktop like I wish for...but at least I got this far..seriously is there anything anyone can figure out??

---

### Post by drphilngood on 2006-11-30
Are you asking where it is at?  /media/sda5

Enter this:

```
df
```

in a terminal and post it here.

---

### Post by PrinceArithon on 2006-11-30
No, I know where it is.  What I want to know is why I don't get an icon on the desktop, or why when I go to Places > Computer; I don't see it with the other drives.

---

### Post by taurus on 2006-11-30
If you want an icon on your desktop, then you need to mount it to /media!!!  Therefore, change this line in /etc/fstab 

```
  /dev/sda5 /fat_files vfat iocharset=utf8,umask=000 0 0
```
to 

```
/dev/sda5 /media/fat_files vfat iocharset=utf8,umask=000 0 0
```
and you need to creat a new mount point for it too...

```
sudo mkdir /media/fat_files
```

---

### Post by PrinceArithon on 2006-11-30
Thank you Taurus...I made such dumb mistake...It works perfectly now.  Thank you.

---

### Post by taurus on 2006-11-30
You're welcome.

---

