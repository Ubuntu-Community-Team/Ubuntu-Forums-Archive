---
title: "Modifying file cache behaviour?"
date: 2008-06-05
forum: General Help
---

### Post by mivo on 2008-06-05
I briefly lost power this morning and it resulted in the loss of quite a bit of data. I'm not actually sure how the outage could corrupt files that had not been modified today, but my main concern is that data was lost that apparently sat in the file cache for days. Is there a way to modify the way that Linux caches files? Can it be turned off? I had most of the lost data backuped (not all), but I never had this happen in a long time with Windows, and it is the second time in half a year that it happened with Ubuntu.

---

### Post by sdennie on 2008-06-05
It's surprising that this would be the case.  What is the output of:

```

cat /proc/sys/vm/dirty_writeback_centisecs
cat /proc/sys/vm/dirty_expire_centisecs

```

If that is set to something reasonable (defaults are around 500 and 3000 centisecs), it's possible that the behavior wasn't caused by linux but by some app having not saved its files.

---

### Post by bingoUV on 2008-06-05
unless you have messed big time with it, there is no way data can sit in file cache without being flushed to the disk for days.

Did you play with journalling options of ext3? See the output of mount to make sure.  Or do you use another filesystem?

---

