---
title: "Recovering deleted files from ext3."
date: 2006-12-01
forum: General Help
---

### Post by Cronjob on 2006-12-01
I meant to delete a single directory from one krusader panel, but unfortunately my mouse was in the OTHER krusader window when I did it, which means that instead of deleting 700mb of data, I deleted 70gb.

It is a 300gb drive formatted as a single ext3 partition and used for storage and all of the data I want to recover is in one specific directory. As soon as I deleted the data, I unmounted the drive.

I've read other posts on this topic here and one suggested using testdrive, but that only recovers lost partitions as far as I can tell. My partition is just fine. I simply need to recover deleted files. All other software that claims to recover files from an ext3 system are Windows applications (gee, that's brilliant). I'm not really sure how they manage to recover ext3, though.

My question is whether this is even possible? Am I correct in understanding that ext3 doesn't merely unlink inodes, but actually zeroes out the files, so my data doesn't exist in any recoverable manner whatsoever (short of shipping it off to a physical recovery service -- the data is important but not THAT important)?

And no, I didn't have backups of this content. It's just a bunch of video (no, not porn) that I would have liked to kept around.

Thanks for any information or guidance you might offer.

---

### Post by evilghost on 2006-12-01
[http://freshmeat.net/projects/unrm/](http://freshmeat.net/projects/unrm/)

---

### Post by Cronjob on 2006-12-01
Unrm only seems to support ext2 (the latest version is from 2001) and as best I can tell from the brief manpage, it apparently copies data from unlinked inodes which you then have to manually chop up (since the start of a file could be in the middle of a block obviously), but since ext3 seems to zero-out a file when it unlinks it, this would not work, correct?

---

### Post by Sef on 2006-12-05
Try [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

