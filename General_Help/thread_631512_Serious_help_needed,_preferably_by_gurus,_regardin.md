---
title: "Serious help needed, preferably by gurus, regarding CD drive problem"
date: 2007-12-04
forum: General Help
---

### Post by Old *ix Geek on 2007-12-04
I posted a thread recently--which got only one response, and it didn't help--about this on the hardware/laptop board, but I really need serious help now and so I'm trying here.

Basically, here's what's happened--but I have no clue how: The DVD/CD-RW drive in my HP dv6000 laptop was fine, I was using it regularly, no problems at all. One day I was copying files to a new, blank CD-RW, and realized something was wrong when the cumulative size of the files well exceeded the capacity of a CD.  I **ls -l**'d /media/cdrom0 and the files--all of them, well over 1GB--were listed.  Of course this made no sense, but there they were. Then I replaced that CD-RW with another new one...and **ls -l** again listed all the files...files that were supposedly on the CD I'd just removed.

At this point it was clear something was very wrong, so I went to /media and found that cdrom0 was now a directory--a normal directory, and all those files were in it.  While I thought I was putting files on a CD, in fact I was putting them in a directory named /media/cdrom0 on the hard drive.  I normally do things from a prompt, but I went to my desktop to see what the CD drive was listed as, and it said "Blank CD."  However, right-clicking on it did NOT yield an "eject" option.

Well, I played around with various things over several days, finally coming to this conclusion: If I insert a commercial CD (such as Roller Coaster Tycoon 2 or a Kodak Picture CD), I first have to 'refresh' a couple times, but then its files are listed and it's perfectly usable.  If I'm at a command line, I have to **ls -l** a couple times before the files show up.  Until then, the files I had copied are shown.

Since the original CD [that I THOUGHT I was writing to] I've tried copying files to other CDs, too, with the same results--they're listed in /media/cdrom0 on the hard drive, but they're not actually on the CD.

As a result of my fiddling around, it now looks like I've lost several hundred files I had downloaded from Clipart.com; they're the files I [thought I] was copying to the CD when the problems started.  Apparently, when I tried writing again to the CD drive, all of those files disappeared.  

I'm scratching my head BIG TIME over all of this, as not only have I never seen anything remotely similar before, but it defies logic! Even the "disappearing" files--if I didn't delete or overwrite them, they should still be...somewhere...but I can't **find** them.

My fstab has not been changed, and here's the pertinent line:
```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I really hope someone can help me figure this out, as I'm fresh out of ideas...

---

### Post by pointone on 2007-12-04
Writing to a CD isn't as simple as just *copying* files to the CD's mount point. You need to use some sort of CD burning software.

/media/cdrom0 is always an actual directory, FYI; that's what a mount point is.

Try this:

```
man mount
```

Read the first few sections VERY CAREFULLY.

---

### Post by harold4 on 2007-12-04
That line looks off.  /dev/hda normally references an entire hard disk.  What does your complete /etc/fstab look like?

---

### Post by Old *ix Geek on 2007-12-04
> **harold4 said:**
> That line looks off.  /dev/hda normally references an entire hard disk.  What does your complete /etc/fstab look like?On this laptop, the hard drive's partitions are named /dev/sda1, /dev/sda2, etc., and /dev/hda really does refer to the CD/DVD drive.

Here's the original fstab as it existed prior to my: 1) wiping windoze off of the drive, and, 2) adding a bunch of entries for networked drives:
```
$ cat fstab.orig
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8a281ba6-65c0-4bf0-af50-3f56c1eb1721 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3642A6DC42A69FDB /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

And here's what it looks like now:
```
$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8a281ba6-65c0-4bf0-af50-3f56c1eb1721 /               ext3    defaults,errors=remount-ro 0       1

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1             /data   ext3    defaults,errors=remount-ro      0       1

//compaq/compaqAll      /mnt/compaqAll  smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
//compaq/compaqusername    /mnt/compaqusername        smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
//compaq/compaqData     /mnt/compaqData smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
//compaq/compaqdoze     /mnt/compaqdoze smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
//compaq/external       /mnt/external   smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0

//hp-a710n/a710_all   /mnt/a710n_all          smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
//hp-a710n/a710n_username        /mnt/a710n_username        smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
//hp-a710n/a710n_data /mnt/a710n_data         smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
//hp-a710n/a710n_username2  /mnt/a710n_username2          smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0

//hpdesktop2/c          /mnt/hpdesktop2         smbfs   credentials=/home/username/.smbpasswd,dmask=777,fmask=777  0       0
```

As you can see, there have been no changes to the CD-RW's line in fstab, hence my confusion.

---

