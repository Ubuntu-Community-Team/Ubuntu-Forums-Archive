---
title: "Can't mount DVD-RW with MEI_UDF filesystem"
date: 2008-02-05
forum: General Help
---

### Post by johncudd on 2008-02-05
I recently bought a Panasonic HDC-DX1 camcorder. It records video on DVD-RW, DVD-RAM, DVD-R, and DVD-R DL. I believe the disc is using a "MEI_UDF" file system. Anyway when I try to mount the disc I get an error that says, "Cannot mount volume. Invalid mount option when attempting to mount the volume 'MEI_UDF'." 

I'd like to be able to try out this tutorial, once I get the disc to read. [http://www.fsckin.com/tag/avchd/]("http://www.fsckin.com/tag/avchd/")

Also here is a copy of my /etc/fstab file.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0c80de31-ddba-44c1-8245-1a3a26ed82ca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=D27CD9037CD8E2F1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=e9eab6f6-15e8-4af7-8897-d12201d6050b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   iso9660,udf user,noauto,exec 0       0
/dev/scd2       /media/cdrom2   iso9660,udf user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#/dev/pktcdvd/0  /media/dvdrecorder  iso9660,udf  rw,user,noauto,notatime,dev  0  0

```

---

### Post by johncudd on 2008-02-05
Bump

---

### Post by johncudd on 2008-02-06
Bump

---

### Post by Sun_Wukong on 2008-02-17
Hi,

I just bought this camera and went into the same problem.

The kernel message is :
Feb 17 21:51:41 kernel: [19410.976873] cdrom: sr0: mrw address space DMA selected
Feb 17 21:51:41 kernel: [19410.978831] cdrom open: mrw_status 'not mrw'
Feb 17 21:51:42 kernel: [19412.116830] UDF-fs: minUDFReadRev=250 (max is 201)

As stated, the disk is in UDF v2.5 format. To this, [Wikipedia]("http://en.wikipedia.org/wiki/Universal_Disk_Format") is very informative : Linux doesn't support yet natively this FileSystem. A patch exists but Ubuntu's default kernels aren't patched. It will happen ... one of these days ;-)

As I've a free partition and I was planning to have a look at some BSDs, I'm gonna install FreeBSD and try this wa as the BSDs recognize this FS. LiveCDs of BSD do exist in case you want to try this lighter way.

Cheers
SW

---

### Post by johncudd on 2008-02-17
Yeah I haven't the guts to try to reconpile my kernel for the file system.

---

### Post by atlya02 on 2008-02-18
I am getting a similar message but on a cd.  I copied some files to try and load BERYL and get "invalid mount option when attempting to mount the volume 'udf volume'."  Please school me.:confused:

---

### Post by Sun_Wukong on 2008-02-19
Well, I installed PC-BSD. That's a really nice and pretty system, running KDE and Compiz out of the box. But.... I wasn't able to read from those damned mini-DVD. ](*,)
I'll try another BSD, one of the 3 main ones, when I've some time.

---

### Post by Sun_Wukong on 2008-02-20
Hi

I managed to access the files on a mini-DVD with a laptop running XP enhanced with Nero InCD.

What's puzzling is that the laptop's optical drive isn't able to read this mini-DVD. I had to plug in the camera in the laptop with a USB cable, then the optical drive embedded in the camera appeared as a new Windows drive that showed the file hierarchy. 

Thus, there are optical drives that can and others that can't. :-(

---

