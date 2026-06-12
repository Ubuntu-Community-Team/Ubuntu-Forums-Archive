---
title: "[SOLVED] fsck died with exit status 8"
date: 2007-06-22
forum: General Help
---

### Post by unebaguettesvp on 2007-06-22
since i've upgraded to feisty from edgy, i get this error while booting up SOMETIMES:

```

 * Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
/dev/hda3 is mounted. e2fsck: Cannot continue, aborting

fsck died with exit status 8
                                                                                                                                  [fail]
 * File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.

```

then, it says if i want to continue the boot sequence press Ctrl-D. so, i do that and i get into fesity, which is where i'm writing from now. but this is REALLY annoying when it happens.

here is that log file:

```

Log of fsck -C -R -A -a 
Fri Jun 22 17:40:29 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/hda3 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Fri Jun 22 17:40:29 2007
----------------

```

also, here is my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7157244b-71bd-4dad-9461-673bd9db47bb /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3	/data	ext3 auto,users,rw 0 1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

also, i noticed that whenever i try to delete something in /data ("/dev/hda3"), i have to delete it permanently. i'm not sure why?

again, this is only happened when i upgraded to feisty. edgy worked flawlessly.

any ideas? thanks for any help!!!

---

### Post by Ultra Magnus on 2007-06-22
I'm not really sure how to help but i found another thread where someone had the same exit error - [http://ubuntuforums.org/showthread.php?t=291890&page=2](http://ubuntuforums.org/showthread.php?t=291890&page=2)

---

### Post by unebaguettesvp on 2007-06-22
yeah, i saw that post. all that person did was change "/dev/sda1" to a UUID. that didn't work for me.

thanks anyway.

can anyone else help? again, i'm not sure why it is inconsistent. thanks in advance.

---

### Post by confused57 on 2007-06-22
It's possible that your UUID(s) have changed when you upgraded?

You could open a terminal, and check your UUID's with:
```
blkid
```

then compare the output of "blkid" with the UUID's in your /etc/fstab and in your menu.lst kernel root UUID.

If they're wrong, then you can just copy& paste the correct one from blkid...you could probably also use UUID to mount your /data partition.

---

### Post by unebaguettesvp on 2007-06-22
i tried changing /dev/hda3 to the UUID to the UUID that i got from blkid and that didn't work either.

menu.lst just has the UUID for the root="UUID of /dev/hda1"

hmmm.... thanks anyway.

any other ideas?

---

### Post by confused57 on 2007-06-22
> **unebaguettesvp said:**
> i tried changing /dev/hda3 to the UUID to the UUID that i got from blkid and that didn't work either.

menu.lst just has the UUID for the root="UUID of /dev/hda1"

hmmm.... thanks anyway.

any other ideas?

Maybe you can find something useful in this guide:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

---

### Post by unebaguettesvp on 2007-06-23
thanks for the help, but i'm still stuck. anyone else have any ideas?

---

### Post by unebaguettesvp on 2007-06-23
so, i decided to avoid doing a fsck check during bootup on that mount and it seems to work so far! in the pass column for /dev/hda3 i put a 0 instead of a 1. that just bypasses the fsck check. hope that helps someone.

---

### Post by exjinn on 2007-06-27
it definitely helped me, thanks a lot! :D

---

