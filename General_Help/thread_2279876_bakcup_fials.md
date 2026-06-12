---
title: "bakcup fials"
date: 2015-05-26
forum: General Help
---

### Post by cybergalvez on 2015-05-26
Hi all, I am have issues with my backup failing. Every time I try to run a backup I get an erro similar to this:

```

Failed to read /tmp/duplicity-HBOD88-tempdir/mktemp-iyqahP-5: (<type 'exceptions.IOError'>, IOError('CRC check failed 0xf62e1b7b != 0x91cc1d6eL',), <traceback object at 0x7f37e1505758>)

```

I know the actual endpoints are meaningless but I'm not sure how to trouble shoot this.  Any help would be appreciated

Jose

---

### Post by Vladlenin5000 on 2015-05-26
How are you doing the backup? What tool? To and/or from where?

---

### Post by cybergalvez on 2015-05-26
I am using the standard "Backup" which is part of Ubuntu Gnome (14.04), which I believe is Duplicity and uses Deja-dup as the back end. I am trying to back up my Home folder to a mounted NFS share on my remove freenas server (in the same room, not the best I know). this has worked in the past , but I am now getting the error I posted in the initial post.

---

### Post by Vladlenin5000 on 2015-05-26
Apparently you are not alone...

[http://askubuntu.com/questions/109895/automatic-backup-keep-failing-how-can-i-force-it-to-run](http://askubuntu.com/questions/109895/automatic-backup-keep-failing-how-can-i-force-it-to-run) <- one or both suggestions might work.
There's also an old bug: [https://bugs.launchpad.net/deja-dup/+bug/875676](https://bugs.launchpad.net/deja-dup/+bug/875676)

---

### Post by cybergalvez on 2015-05-26
I saw the launchpad bug, right now I am trying to make a new fresh backup in a new location, if that works, I'll just delete the old backups and just use the new set.  Keeping my fingers crossed.

just an update:  creating a new endpoint did the trick, not sure what corrupted the old backup, but it really doesn't matter now, the backup is running smoothly again

---

