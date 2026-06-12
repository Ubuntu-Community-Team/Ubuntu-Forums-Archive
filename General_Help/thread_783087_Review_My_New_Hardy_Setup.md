---
title: "Review My New Hardy Setup"
date: 2008-05-05
forum: General Help
---

### Post by WelterPelter on 2008-05-05
Hi. I had some trouble upgrading from G to H (actually it was a total catastrophe), and so decided to do a fresh install. That has worked out well. Everything seems to be running nicely.

After the fresh install, I realized that I had not created a separate partition for my /home, which I normally like to do. So I went ahead and did that, and -- after tinkering with it a bit -- it all seems to be working properly.

However I do not have total confidence in my set-up. Everything is functioning correctly so far, but I'd like to make sure it's set up the way it should be. I have two questions I'd like to put out there, just to make sure that my set-up is solid. 

FIRST: The gvs-fuse daemon (whatever that is) still thinks my /home is in its old location. How do I change that? What would I want this daemon for anyway? 

SECOND: Here is my current fstab, which I edited by hand. It works, but I'm open to comments about best practices, etc. You'll notice that I'm running three drives on this machine, as usual.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a07ba07c-defa-47a1-8a38-7e67148f3165 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=77b81305-9331-4c71-89d2-b657bb5379c7 none            swap    sw              0       0

/dev/sdc1    /data     ext3    defaults    0       0
/dev/sdc2    /home     ext3    defaults    0       0

/dev/sdb1    /windows    vfat    defaults

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Thanks in advance for any pointers.

---

### Post by TeoBigusGeekus on 2008-05-05
About your fstab:
Change the last zeros of /data and /home to 2. 
In this way, the partitions will be checked for errors on startup occasionally along with your file system.

---

### Post by WelterPelter on 2008-05-05
> **TeoBigusGeekus said:**
> About your fstab:
Change the last zeros of /data and /home to 2. 
In this way, the partitions will be checked for errors on startup occasionally along with your file system.

Thanks. I was wondering about that.
Change made.

---

