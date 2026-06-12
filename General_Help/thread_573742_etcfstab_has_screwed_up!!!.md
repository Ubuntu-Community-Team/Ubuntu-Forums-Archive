---
title: "/etc/fstab has screwed up!!!"
date: 2007-10-11
forum: General Help
---

### Post by j.miller565 on 2007-10-11
I found out that I've totally screwed up my fstab.

This is what I find in it:

```

ldcard include/config/proc/fs.h) \
    $(wildcard include/config/debug/pagealloc.h) \
  include/linux/capability.h \
  include/linux/rbtree.h \
  include/linux/prio_tree.h \
  include/linux/fs.h \
    $(wildcard include/config/dnotify.h) \
    $(wildcard include/config/quota.h) \
    $(wildcard include/config/inotify.h) \
    $(wildcard include/config/security.h) \
    $(wildcard include/config/epoll.h) \
    $(wildcard include/config/auditsyscall.h) \
    $(wildcard include/config/block.h) \
    $(wildcard include/config/fs/xip.h) \
    $(wildcard include/config/migration.h) \
  include/linux/limits.h \
  include/linux/ioctl.h \
  include/asm/ioctl.h \
```

Can someone please tell me if I can fix this problem.  The good thing is that my harddrive still boots up in Linux.


J.miller565

---

### Post by odiseo77 on 2007-10-11
wow, this is really weird! seems like you copied some code from some program into your /etc/fstab file. Ok, what first comes to my mind is that maybe gedit (or anyother editing software you used) automatically backed up your /etc/fstab file when you screwed it, so let's try to find it out:

```
cd /etc
ls -la *fstab*
```

If you see some file named something like **fstab~**, then you probably found your backup (all you would have to do is to open it to verify its contents and copy them to your current /etc/fstab).

If you don't have a backup, then the solution might be a bit trickier and difficult, but I'm hoping you have a backup :)

---

### Post by j.miller565 on 2007-10-12
Cheers well I did find fstab~.

```
simon@green-kubuntu-desktop:~$ cd /etc
simon@green-kubuntu-desktop:/etc$ ls -la fstab*
-rw-r--r-- 1 root root 664 2007-10-04 19:29 fstab
-rw-r--r-- 1 root root 733 2007-10-04 17:21 fstab~
-rw-r--r-- 1 root root  37 2007-04-17 17:19 fstab.pre-uuid

```

so now, do i just paste the contents of fstab~ into fstab?

---

### Post by odiseo77 on 2007-10-12
First, verify the contents of your **fstab~** file (check that it matches your partitions, devices, etc); if it's ok, then open both, /etc/fstab and /etc/fstab~, remove all the weird lines of your current /etc/fstab file and copy the contents of your /etc/fstab~ file into the first one (the blank /etc/fstab).

Greetings.

---

### Post by j.miller565 on 2007-10-12
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 / ext3
noatime,data=writeback 0 1
UUID=309b12f3-5fe9-4205-86da-467f415afbb1 /               ext3    defaults,errors=remount-ro,data=writeback 0       1
# /dev/hda5
UUID=ff110b00-ff99-47ad-9f9d-742d3e1f4e44 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto      0       0
/dev/sdb2 /media/videopodcasts ext3 defaults                0       2
```

I reckon this looks better doesn't it lol ?
This was the one in fstab~

---

### Post by j.miller565 on 2007-10-12
Oh man thank you so much odiseo77. Everything works normally now.
Thanks again man!!!

---

