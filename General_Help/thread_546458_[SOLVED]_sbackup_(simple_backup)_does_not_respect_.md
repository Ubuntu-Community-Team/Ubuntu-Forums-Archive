---
title: "[SOLVED] sbackup (simple backup) does not respect symlinks?"
date: 2007-09-08
forum: General Help
---

### Post by bvz on 2007-09-08
Hi there,

I have finally finished installing ubuntu (and replacing XP).  I still have XP on the machine (my room mate's machine) and she will be switching back and forth for a while so I did the following:

I sym-linked her windows Desktop to be her ubuntu Desktop.  Same with her My Documents folder.  Both are on ntfs partitions which are read/write capable.

sbackup works more or less correctly except for the following:  sbackup seems to copy a single file (the symlink file) instead of the contents of the directory that it links to.

Any ideas?

ben

---

### Post by ruibernardo on 2007-09-08
I think that simlinks don't work very well with NTFS. Maybe you could try "mount --bind" to do that. From the "man mount" page:

```
mount --bind olddir newdir
       After this call the same contents is accessible in two places.  One can
       also remount a single file (on a single file).
```

---

### Post by bvz on 2007-09-09
I'll look into it.  Thanks.

I have to admit to being a bit frightened of changing too much right now though...  most everything seems to work and I don't want to rock the boat too much.  I'd rather give up the auto-backup than have to deal with other weirdness.

---

### Post by ruibernardo on 2007-09-09
Well, if you don't want to do that, and you already have the NTFS partition mounted, you could specify explicitly in sbackup to backup that folder. You can do that in the "include" tab (taken from [http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html))

[IMG]http://www.debianadmin.com/images/sbackup/4.png[/IMG]

Add the folder /media/windows/the/path/for/the/users/desktop by clicking on "Add Directory" button.

Is this what you want?

---

### Post by bvz on 2007-09-09
Duh!  I didn't even think of that.  Of course.

I am trying it now and I will let you know.  Thanks!

ben

---

### Post by bvz on 2007-09-09
That worked like a charm!  Thanks.

---

