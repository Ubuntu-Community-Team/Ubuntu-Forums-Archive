---
title: "fd0 not found in fstab?"
date: 2006-10-15
forum: General Help
---

### Post by Bartender on 2006-10-15
Trying to follow catlett's directions to make grub floppy
[http://www.ubuntuforums.org/showthread.php?t=224345&highlight=grub+install](http://www.ubuntuforums.org/showthread.php?t=224345&highlight=grub+install)

Got past the first entry but not the second...

bpbar@bpbar-desktop:~$ sudo mkfs /dev/fd0

mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
184 inodes, 1440 blocks
72 blocks (5.00%) reserved for the super user
First data block=1
1 block group
8192 blocks per group, 8192 fragments per group
184 inodes per group

Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 26 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
bpbar@bpbar-desktop:~$ sudo mount /media/floppy0
mount: can't find /media/floppy0 in /etc/fstab or /etc/mtab

Can't find the floppy drive in fstab?  How do I fix this?

---

### Post by nereid on 2006-10-15
Just insert it into the fstab file. This is just for convenience and some automation.

Try

```

mount /dev/fd0 /media/floppy0

```

to mount your floppy without a fstab entry.

---

### Post by Bartender on 2006-10-15
Entered
sudo gedit /etc/fstab

There was no entry for fd0.

Added to the bottom of fstab: 
/dev/fd0   media/floppy0  auto  rw, user, noauto   0   0
I typed in the line exactly as it was expressed in "Beginning Ubuntu" book.

Now when I try 
sudo mount /media/floppy0
I get (mntent): line 8 in /etc/fstab is bad
mount: can't find /media/floppy0 in /etc/fstab or /etc/mtab

Could someone please paste in their fstab floppy entry?  That might help.    
Thanks

---

### Post by NoWhereMan on 2006-10-15
maybe you wrote media/floppy0 instead of /media/floppy0 ? :-k

---

### Post by Bartender on 2006-10-15
I put spaces between rw & user & noauto 
Duh

---

