---
title: "Quick question about Reiserfs"
date: 2007-03-23
forum: General Help
---

### Post by noxxle on 2007-03-23
Been using ext3 for a long time now. I've heard good things about reiserfs, particularly that its very fast. There is one thing that, if true, scares me about reiserfs. A friend told me that if you are working on a paper and for some reason your system freezes (suppose the only way to shut down, is a hard reset), you will lose that paper. Is that true? If I am writing my thesis should I avoid doing it on Reiserfs....?

---

### Post by 1/0 on 2007-03-23
I've used reiserfs for a long while and I can't say that I noticed any greatly increased speed. I had some errors that could be caused by reiserfs so I switched back to ext3. I haven't had any losses when rebooting though. 

I'm not sure if there is any development of reiserfs, since the founder got arrested for the murder of his wife. There is development of a new ext4 file system and there's alway XFS that's fast and reliable. I would, IMHO, stick to ext2, ext3 or XFS.

---

### Post by noxxle on 2007-03-23
I've heard xfs is even more likely to lose data and corrupted it during unexpected shutdowns.

---

### Post by 1/0 on 2007-03-23
Yes, I guess you're right about xfs but its fast. With that concern about stability I'd stay with ext3 and maybe configure/tune ext3 to work faster (as in enabling full journaling, enabling directory indexing and maybe disabling the boot checks).

Ext4 is much faster but new.

---

### Post by esaym on 2007-03-27
ext3 is a very good files system.  If you want faster transfers then you don't need to be playing with reiser or xfs, you need to be setting up an external journal for ext3.  Then it will be just as fast as ext2, which is alot faster then reiser.  Reiser is only marginally faster then ext3 anyway.

---

