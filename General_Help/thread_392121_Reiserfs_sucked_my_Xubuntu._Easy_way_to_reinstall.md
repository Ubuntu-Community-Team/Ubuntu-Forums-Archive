---
title: "Reiserfs sucked my Xubuntu. Easy way to reinstall?"
date: 2007-03-24
forum: General Help
---

### Post by cd-r80 on 2007-03-24
Reiserfs sucked my Xubuntu /root . /home seems to be ok? Easiest way to reinstall and leave home untouched? No more Reiserfs! Later get rid off reiserfs home... Well perhaps just install a new from here Live CD. Can I make dist-upgrade at the same time? I have no bad blocks.

---

### Post by profXavier on 2007-03-26
If you could, please explain your symptoms a bit more.  I have been having issues all weekend with my partitions (reiser) and I would be interested to hear if yours are the same.

What have you done to solve your issues?

---

### Post by cd-r80 on 2007-03-26
Files in my root partition got corrupted. I did not have power failure, but memtest86 showed a faulty memory. Perhaps that was the reason or can it be?  I could not boot because of errors of many basic shell commands missing. X did not start. I ended in console mode, but I did not have even ls command. I tried to do fsck.reiserfs, --fix-fixable, finally --rebuild-tree, but no help. badblocks I did not found. I don't remember exact errors:

"search_by_key: invalid format found in block 43512. Fsck?
vs-13070: reiserfs_read_inode2: i/o failure occurred trying to find stat data of "

I moved not corrupted /home to my fileserver & I installed a new with ext3. I had used ReiserFs for about 6 years...

---

