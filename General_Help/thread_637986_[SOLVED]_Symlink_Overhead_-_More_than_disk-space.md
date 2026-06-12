---
title: "[SOLVED] Symlink Overhead - More than disk-space?"
date: 2007-12-11
forum: General Help
---

### Post by Rick Myers on 2007-12-11
Is there any operational overhead associated with symlinks other than disk-space?

I'm trying to relocate a PostgreSQL database store to another drive and am wondering if by doing so I'll be utilizing additional memory or CPU cycles.

I realize there are other ways of relocating the data-store, but this question has come up and it has me curious.

---

### Post by bingoUV on 2007-12-11
There is the overhead of first locating the symlink inode. Then learning that the file is actually somewhere else. Then locating the linked file (which might again be a symlink, but you get the idea).

Hard links would not have this overhead, but you may not have this option.

---

### Post by dcstar on 2007-12-11
> **bingoUV said:**
> There is the overhead of first locating the symlink inode. Then learning that the file is actually somewhere else. Then locating the linked file (which might again be a symlink, but you get the idea).

Hard links would not have this overhead, but you may not have this option.

Hardlinks are only available on the same filesystem (as they contain pointers to the physical disk blocks), symlinks can cross all mounted filesystems.

---

### Post by Rick Myers on 2007-12-12
> **bingoUV said:**
> There is the overhead of first locating the symlink inode. Then learning that the file is actually somewhere else. Then locating the linked file (which might again be a symlink, but you get the idea).

Hard links would not have this overhead, but you may not have this option.

Is the effect cumulative? The web site using the database receives a lot of traffic. I'm concerned the machine may slow if we use a symlink versus reconfigure PostgreSQL. My intent was not to turn this into a discussion about PostgreSQL but rather to determine if the use of symlinks in a high traffic environment will impact performance.

---

### Post by bingoUV on 2007-12-12
Cumulative over what? If you mean a long train of symlinks like
```

link1 -> link2 -> link3 -> link4 -> realFile

```
is worse than a single symlink, yes.

If you absolutely have to have the best performance, no symlinks for you. But it may not matter enough to warrant a reconfiguration of the database, in which case it is fine.

---

### Post by Rick Myers on 2007-12-12
Cumulative like;

WebUser1 > symlink > database
WebUser2 > symlink > database
etc.

Does it work like: hit symlink - uses resource, overhead immediately released? or uses resource, overhead accumulates until user goes away?

---

