---
title: "bad xfs performance?"
date: 2007-04-25
forum: General Help
---

### Post by 5hundy on 2007-04-25
I just did a clean install of Feisty and decided to try xfs based on [this]("http://www.debian-administration.org/articles/388") article. After I got the system set up I found that my work-related db scripts were running much slower than I'm used to. I did some benchmarking and the _exact same drive_ gets a **7x** performance degradation by using xfs instead of ext3 with my mysql and sqlite tests. Can anyone explain this? My tests basically did a few thousand writes to the same db.

---

### Post by BoneKracker on 2007-04-25
That's a pretty severe drop.

XFS can be a great filesystem.  It's touchy (susceptible to corruption) and has a lot of tuning options that need to be properly set for it to achieve maximum performance.

---

### Post by kilou on 2007-05-17
I've also seen many articles saying that XFS was one of the fastest filesystem. However I came across this test which is linked in the article you mentionned:

[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

The author still seem to recommend XFS for performances but seeing the results I don't really understand why. It seems to me in this test that EXT3 is much better for instance. The only area where it lags seems to be the filesystem creation time but who cares about that since you only do it once. Even on large file operations it appears on this test that EXT3 was faster than XFS so I don't understand why XFS would be recommended in the end.

I also wanted to format my system and reinstall Ubuntu on XFS but now I think I'll stay with my tuned EXT3.

---

### Post by BoneKracker on 2007-05-17
I would be careful not to put too much stock in one set of tests, particularly unscientific ones.  While the author performed a fairly broad array of actions, he did not vary the storage architecture at all.

My understanding is that XFS is highly preferable for a limited set of conditions that fall outside the use cases for virtually all desktops and many servers.  Similarly, other filesystems have their strengths and weaknesses.

His test results do bear out the conventional wisdom that ext3 is a good all-round choice.  It also speaks well for JFS, although there are not as many data points available (globally I mean) to back up the case for JFS.

---

### Post by fanatik on 2007-05-17
did you modify hdparm settings before or after installing XFS ?

---

