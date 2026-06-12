---
title: "Can't unmount because resources busy, but lsof doesn't show any use"
date: 2018-10-01
forum: General Help
---

### Post by SagaciousKJB on 2018-10-01
This happens a lot on my system and I don't understand.  I have some volume mounted and need to unmount, but it tells me that it's busy.  I then try to do lsof but it doesn't list any use of the mount point or drive in question.  So how am I supposed to keep it from being used?

```
root@AMD:~# umount /mnt/backups/
umount: /mnt/backups/: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
root@AMD:~# lsof | grep /mnt/backups/
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
root@AMD:~# lsof | grep /dev/sde1
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
root@AMD:~# 

```

So what am I supposed to do at this point?

---

### Post by The Cog on 2018-10-02
Make sure you don't have a file manager or a command prompt open in that directory.

Make sure it has finished writing from cache - use **iostat** to see if it's busy writing, or use the command **sync** and wait for that to return.

You could try "**[FONT=Courier New]umount -l /mnt/backups/[/FONT]**" That has worked for me in the past, although I guess there is the possibility of removing it while it is still busy and causing filesystem damage.

---

### Post by SagaciousKJB on 2018-10-02
> **The Cog said:**
> Make sure you don't have a file manager or a command prompt open in that directory.

Make sure it has finished writing from cache - use **iostat** to see if it's busy writing, or use the command **sync** and wait for that to return.

You could try "**[FONT=Courier New]umount -l /mnt/backups/[/FONT]**" That has worked for me in the past, although I guess there is the possibility of removing it while it is still busy and causing filesystem damage.

Thanks, umount -l worked but I'm going to give sync a try next time.  I just don't know that it was something like that this time around, because I had been waiting for several minutes already.

---

