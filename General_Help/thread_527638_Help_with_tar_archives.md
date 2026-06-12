---
title: "Help with tar archives"
date: 2007-08-16
forum: General Help
---

### Post by Ozor Mox on 2007-08-16
If I create a tar archive on my external hard drive by running

```
sudo tar -cvvpf /media/disk/backup.tar /home/me/Desktop/MyFolder
```

it basically (after a long time) creates a big file with all of the contents of MyFolder in it. Can I then incrementally add/update only the changed files to the tar archive by doing

```
sudo tar -uvvpf /media/disk/backup.tar /home/me/Desktop/MyFolder
```

?

I have tried this, but firstly I could not open the tar using the archive manager as it just read it for hours and never displayed...and secondly when I tried doing the update tar command it just sat there at the command line and never actually completed.

I have tried doing this on a smaller set of files (MyFolder is about 25.2 GB) and it seemed to work, although the update tar command would list every file each time, even if it hadn't changed.

Am I thinking about this the right way? I know rdiff-backup and rsync are probably better solutions for this sort of thing, but I'm trying this out because I need to copy my backup to a third location. If anyone has any better ideas, I'd love to hear them!

Thanks!

---

### Post by Ozor Mox on 2007-08-17
This is really annoying. I messed around with it some more but no matter what I do, using the u option for update archive just writes another copy of every file to the archive so I end up with duplicates everywhere, even though those files haven't changed. It says in the man page that update will only append files that are newer than those in the archive.

Anyone got any ideas or can tell me if I'm doing something stupid?

---

### Post by cdtech on 2007-08-26
> **Ozor Mox said:**
> This is really annoying. I messed around with it some more but no matter what I do, using the u option for update archive just writes another copy of every file to the archive so I end up with duplicates everywhere, even though those files haven't changed. It says in the man page that update will only append files that are newer than those in the archive.

Anyone got any ideas or can tell me if I'm doing something stupid?

I use the --newer flag (-N) for incremental backups; "tar --newer", but I also run this from a script which creates a variable of the last full backup date.

---

### Post by cdtech on 2008-01-02
Here is a script I wrote for my backup using cron, maybe this can be of some help.

[[COLOR="DarkRed"].:: backup script ::.[/COLOR]]("http://www.bobs.homelinux.com/code/backup-script/mytarbackup")

Hope this helps.

P.S. I backup to a 4G USB stick, hense the mount and unmount

---

