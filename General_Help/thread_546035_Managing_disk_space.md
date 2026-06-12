---
title: "Managing disk space"
date: 2007-09-08
forum: General Help
---

### Post by Vadi on 2007-09-08
Okay, I've messed up somewhat, and my ubuntu patrition was filled up to nearly 100% with a backup file I was making, making it unlogin-able.

So, eh, I loaded the LiveCD, went to my media/disk/var/backup, deleted 6GB worth of backups. It said they're too big to fit into Trash, fine by me.

Rebooted, and... still got the error that my disk is full.

LiveCD again. Nothing in backups now. I launched the Disk Usage Analyzer, it's saying I have 99.#% free. Went to my .Trash, wiped that, went to root's .Trash, wiped that too. 99.3% now.

What I'm confused about... I already deleted 6GB worth of backup files. Shouldn't there be less than 99% taken now?

I just don't know what else to delete to make my ubuntu bootable :(

---

### Post by Vadi on 2007-09-08
Okay, I also deleted a 2.5GB file, my home dir shrunk by 2.5GB as expected, but my total file usage didn't!

How can I have it so it's -really- gone? As in, not in the trash even?

---

### Post by Vadi on 2007-09-08
I read this on Wikipedia about ext3...

```
Undeletion

Unlike ext2, ext3 zeroes out block pointers in the inodes of deleted files. It does this to simplify read-write access to the filesystem when the journal is being replayed after an unclean mount. This, however, effectively prevents files from being undeleted. The user's only recourse is to grep the hard drive for data known to signal the start and end of the file. This provides slightly more secure deletion than ext2, which can be either an advantage or a disadvantage.
```

... is there any way I can... "clean up" my patrition?

---

### Post by Vadi on 2007-09-08
Can anyone help?

My ubuntu is still not login-able.

---

