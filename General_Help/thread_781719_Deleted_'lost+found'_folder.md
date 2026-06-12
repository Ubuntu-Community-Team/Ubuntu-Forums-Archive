---
title: "Deleted 'lost+found' folder"
date: 2008-05-04
forum: General Help
---

### Post by d_j_ernesto on 2008-05-04
Hello All,
   New to Ubuntu, 7.10. Created storage folder on 2nd HDD, /dedv/sdb1, ff ext3. When I opened it, it showed 1 folder, 'lost+found', taking up all the space, and telling me I did not have permission to open it. I didn't know why it was there, so I changed its permissions and deleted it. I have experienced no ill effects thus far.

Is that file somehow linked to the 'lost+found' in /dev/sda? the one in /sda says 'contents unreadable' under file properties, and has the boxed 'X' emblem on it. Is that file still intact?

I was not even aware of the 'lost+found' folder until I deleted it from /sdb1.

Thanks in advance for your help.

Ernesto

system:
Dell DimensionXPS R_ w/Celeron 1.1 GHz on slot1 to socket 370 adapter
384 MB RAM (max installed)
/sda 40 GiB Samsung HDD
/sdb 60 GiB Western Digital HDD
A13 BIOS (2000)
Ubuntu 7.10 GG
nVidia video card 16 MB SDRAM
4x DVD-ROM
6x CD-RW
floppy
200W PSU

---

### Post by jimbob on 2008-05-04
The lost+found folder is created on every Unix (read Linux) partition when it is created I believe.  No it is not linked anywhere and I wouldn't worry about it.  The system will probably create a new one if it ever needs it. But don't delete it again - just ignore it. Google for a more detailed explanation if you want.

---

### Post by d_j_ernesto on 2008-05-04
Thanks. That makes me feel better.

Ernesto

---

### Post by Vivaldi Gloria on 2008-05-04
During boot, fsck will go through the disks and try to recover corrupt files. If found, any recovered file will be placed in lost & found. Generally they are rubbish.

---

### Post by mannheim on 2008-05-04
You can recreate the "lost+found" directory for sdb1 by doing the following in a terminal (replacing <xxxx> with the directory at which sdb1 is mounted:
```
cd <xxxx>
sudo mklost+found
```

The point of the lost+found directory (as explained above) is to have a place in which "fsck" can put any recovered files that it might find when it finds problems with a filesystem. The lost+found directory has space preallocated for directory entries: this means that no more space need be allocated for these directory entries during the recovery process, so reducing the risk of creating further problems (I think).

---

