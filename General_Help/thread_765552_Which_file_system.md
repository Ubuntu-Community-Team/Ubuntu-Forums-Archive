---
title: "Which file system?"
date: 2008-04-24
forum: General Help
---

### Post by shamusl on 2008-04-24
Installing Ubuntu right now, and wondering what file system I should use. Thanks. - Shamus

---

### Post by BatsotO on 2008-04-24
what's wrong with ext3? millions use it and fine with it.

---

### Post by shamusl on 2008-04-24
Well, it's just that I've heard that XFS is faster, is this true?

---

### Post by retrow on 2008-04-24
I usually go with ReiserFS. However its easy to run fsck on ext2/ext3 type systems. For root partition I would recommend ReiserFS. However if you have additional partitions, you can format them under ext2/ext3.

---

### Post by syxbit on 2008-04-24
i'd stick with tried and tested ext3, at least until ext4 comes along.
and, we always have btrfs coming next year to compete with zfs :)

---

### Post by BatsotO on 2008-04-24
> **shamusl said:**
> Well, it's just that I've heard that XFS is faster, is this true?

Maybe, but I believe the difference is not so big. It's not like having some more rams plugged in.

---

