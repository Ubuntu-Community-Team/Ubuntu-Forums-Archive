---
title: "[SOLVED] How to free used up 5% of ext3 partition"
date: 2007-11-17
forum: General Help
---

### Post by TidusBlade on 2007-11-17
Im using a 500GB Internal HD as storage, so I used it fully to create an ext3 partition, of which, the usual 5% was taken up, and I want to be able to use it somehow.
Thanks :popcorn:

---

### Post by wolfger on 2007-11-17
Well, I'm guessing that's the amount taken up by the journaled file system. If you would rather have the space than the journal, use a non-journaling file system like ext2.

---

### Post by HermanAB on 2007-11-17
I use IBM's JFS. It only has 0.2% overhead, compared to the 7% of Ext3.  The bigger the disk drive, the bigger the savings.

---

### Post by TidusBlade on 2007-11-17
Thanks :) Ill try using ext2. Any idea on ext4 aswell?
JFS also sounds good, but no idea on how to create a JFS partition :S

---

### Post by JBAlaska on 2007-11-17
You might want to check out XFS as well as JFS, both are very fast at deleting big files unlike ext2.

You can use gparted on the livecd to format to either of those file systems.

---

### Post by TidusBlade on 2007-11-17
Oh, thanks for pointing that out JB :) I deal with big files so Ill try out either JFS and XFS.

---

### Post by pjkoczan on 2007-11-17
Much of that used space is metadata, esp. inodes. The journal takes up a fair amount, too, but I wouldn't recommend a non-journaled filesystem unless you like the threat of filesystem corruption.

From what little I've read about JFS, it only does metadata journaling (ext3 also journals block data), and inode space is dynamic, whereas ext3's is static (set on fs creation). Correct me if I'm wrong, but I think this means that while there is more free space, more is used when creating a new file since the inode has to be allocated as well. This would be a huge win with few large files, but a wash with many small files. Take this with a grain of salt, as I haven't used it enough to have opinions on it.

---

### Post by TidusBlade on 2007-11-18
Thanks for mentioningthat Pjkoczan ;) Im just about to change it, and Ill probably stick to ext3, since I have never had problems with it :) But does anyboy have ideas on ext4 ?

---

### Post by anaconda on 2007-11-18
No, no, no, noooo..

The 5% is reserved for root (unnecessarily) and the amount can be adjusted to 0% with: (if I remember correctly) 
```
tune2fs -m 0 /dev/xxx
```

another way to use the reserved 5% is to make root user use that..

---

### Post by .nedberg on 2007-11-19
> **anaconda said:**
> No, no, no, noooo..

The 5% is reserved for root (unnecessarily) and the amount can be adjusted to 0% with: (if I remember correctly) 
```
tune2fs -m 0 /dev/xxx
```

another way to use the reserved 5% is to make root user use that..

Can this be (safely) done on a mounted partition?

---

### Post by atlfalcons866 on 2007-11-19
> **.nedberg said:**
> Can this be (safely) done on a mounted partition?

Yes i did on my /home because i knew i would never log in to my /home as root. I use JFS for my / and my computer is at least 10% faster than using ext3. BUt i do use ext3 on my /home with block journaling.

---

### Post by atlfalcons866 on 2007-11-19
ext3 takes forever to delete large files compared to jfs. It took 4 minutes just to delete a 75GB backup of my external drive. JFS tooks like 4 seconds. I plan on switching my /home to jfs next time i buy a new hard drive thats is 400GB because e2fscks takes forever to fsck.

---

