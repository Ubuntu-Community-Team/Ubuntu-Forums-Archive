---
title: "Hard drive won't mount automatically"
date: 2007-01-15
forum: General Help
---

### Post by mapleshade on 2007-01-15
Here's my fstab:

#/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2	/               ext3    defaults,errors=remount-ro 0       1
/dev/sda1	/var/media/movies   xfs     defaults        0       2
/dev/hda3	/var            xfs     defaults        0       2
/dev/sdb1	/var/media      xfs     defaults        0       2
/dev/hda1	none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

If I ```
sudo mount -a
```, sda1 only mounts for the session.  When I reboot sda1 mounts as /dev/sda1 instead of /var/media/movies.  How can I get sda1 to mount as /var/media/movies at boot?

---

### Post by mapleshade on 2007-01-17
Anyone?  I can't figure out why it would mount with sudo mount -a, but not at boot.  The permissions are the same as sdb1 which mounts fine.

---

### Post by bodhi.zazen on 2007-01-17
Not sure, but is this a removable device ?

perhaps it is your mount point ??

Try changing to /var/movies

Just a shot in the dark mind you :)

---

### Post by mapleshade on 2007-01-17
It is not a removable device.  It's the Maxtor HD listed in my signature.  I'm not quite sure how the mount point could affect it, but I'll give it a try.  It will mount to /var/media/movies if I sudo mount -a.  It just won't do it automatically on boot.

---

### Post by bodhi.zazen on 2007-01-17
My guess is you are mounting /dev/sdb1 to /var/media

So, at boot sda1 is mounted to /var/media/movies, no problem here

... but then the directory /var/media changes when sdb1 is mounted to /var/media

(mounting sdb1 to /var/media overwrites the /media/var/movies directory)

... and then mount -a re-mounts sda1 in /var/media which is /sdb1

I'll bet you a nickel if rather then mount -a you umount /dev/sdb1 and then ls /var/media you will in fact see /var/media/music :) 

So if you do not mount sda1 in a sub-directory of sdb1 you should be OK ...

If that makes sense ....

HTH

---

### Post by mapleshade on 2007-01-17
> **bodhi.zazen said:**
> My guess is you are mounting /dev/sdb1 to /var/media
So if you do not mount sda1 in a sub-directory of sdb1 you should be OK ...
If that makes sense ....
HTH

That does make sense.  I assume that since sda1 is mounting before sdb1, I could just change the drives around on the mobo and switch sda and sdb in fstab.

This may work.  Thanks.

---

### Post by mapleshade on 2007-01-17
OK, so I switched sda1 and sdb1 on the mobo and in fstab, same prob.  I then changed them to ~brian/media and ~brian/media/movies in fstab.  I umonted both of them and did a mount -a.  i got an error that ~brian/media/movies did not exist.  I then did mount -a again and they were fine.  I rebooted and sdb1 didn't mount to ~brian/media/movies.  i think the problem is that sda1 doesn't  mount quickly enough to produce the directory /movies for sdb1 to mount to.  That's why it only works after sda1 has finished mounting.  is there any way to put a delay in to let sda1 mount before sdb1 tries to mount?  Both drives are my media drives, one is reserved for movies and I'd really like them under the same directory (i.e. i want to have one mounted in the other).

---

### Post by bodhi.zazen on 2007-01-18
> **mapleshade said:**
> OK, so I switched sda1 and sdb1 on the mobo and in fstab, same prob.  I then changed them to ~brian/media and ~brian/media/movies in fstab.  I umonted both of them and did a mount -a.  i got an error that ~brian/media/movies did not exist.  I then did mount -a again and they were fine.  I rebooted and sdb1 didn't mount to ~brian/media/movies.  i think the problem is that sda1 doesn't  mount quickly enough to produce the directory /movies for sdb1 to mount to.  That's why it only works after sda1 has finished mounting.  is there any way to put a delay in to let sda1 mount before sdb1 tries to mount?  Both drives are my media drives, one is reserved for movies and I'd really like them under the same directory (i.e. i want to have one mounted in the other).

Well, you could modify rc.local

```
gksudo gedit /etc/rc.local
```

Add:

mount -a

or 

mount /var/media/movies

just above exit 0

---

### Post by mapleshade on 2007-01-18
That worked.  Probably not the cleanest way to have to do things, but it works.  Thanks for the help.

---

### Post by bodhi.zazen on 2007-01-18
8)

It was a lucky guess :twisted:

---

