---
title: "Fastest way to rm a directory tree with 1000s of hardlinks"
date: 2007-11-14
forum: General Help
---

### Post by mlambie on 2007-11-14
I'm using a combination of rsync and cp -al to keep backups in rotation for the day. This means that at the beginning of each process I delete the oldest backup with:

```
rm -rf /data/backup.007
```

This takes a long, long time (around 5-10 minutes) and I was wondering if there was a faster way to remove the directory. It contains mostly hardlinks - one for every file on a normal Ubuntu root filesystem, so that'll be in the "tens of thousands" region.

Is there a faster way?

---

### Post by omicist on 2007-11-15
A link you may find helpful:

[http://grokbase.com/groups/centos.org/centos/topics/2007/09/29/centos-silly-question-anything-faster-than-rm/fR7yMWLn8Qj5OVF6XcJTYUfVz94](http://grokbase.com/groups/centos.org/centos/topics/2007/09/29/centos-silly-question-anything-faster-than-rm/fR7yMWLn8Qj5OVF6XcJTYUfVz94)

---

### Post by mlambie on 2007-11-15
Thanks for the link.

---

