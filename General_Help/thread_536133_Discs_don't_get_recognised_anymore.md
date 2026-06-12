---
title: "Discs don't get recognised anymore"
date: 2007-08-27
forum: General Help
---

### Post by dean20007 on 2007-08-27
Hi

Tonight I tried to burn a data cd using brasero. It appeared to complete after taking quite a long time, but now whenever I put a cd in the drive the drive seems to struggle and doesn't get recognized bu Ubuntu. 

1) I can get DVDs and CDs to play running gmplayer via terminal however even in Places menu where I would expect see DVD or CD menu entry I get CD/DVD creator instead 
2) putting a blank CD in the drive (or any data cd) it won't get recognized and I can't browse the disk either I get told there is no disk in the drive. 

here is my fstab. Can anyone help
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1a77410d-bb22-40f9-bc81-884fde112d44 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=E6488002487FCFB3 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=843CBAE23CBACE84 /media/sda4     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=c5838b8c-d01d-43af-8868-088eae20f15c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by dean20007 on 2007-08-27
In addition to these problems now when I put a cd in the drive continually seems to be trying to read the disc.

---

### Post by dean20007 on 2007-08-31
*BUMP*

In the hope someone can help. This is really starting to annoy me, so much so my hand is subconsciously reaching for that XP cd again!!

---

