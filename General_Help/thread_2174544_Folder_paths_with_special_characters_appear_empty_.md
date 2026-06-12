---
title: "Folder paths with special characters appear empty over Samba"
date: 2013-09-15
forum: General Help
---

### Post by jamesisin on 2013-09-15
Setup:

ShareA - Long time share containing large file structure
ShareB - Brand new share containing specific links to files in ShareA

Both shares are on the same partition (in adjacent folders).

In order to get the links in ShareB to function I enabled this in smb.conf:

```
unix extensions = no
wide links = yes
```

This caused special characters to return useless file names (maybe 0Kfng or similar) back on ShareA.  So I found that I could turn that "feature" off with this:

```
mangled names = no
```

This returned ShareA to using actual file paths regardless of special characters.  Now the folders on ShareA which have special characters (like : or similar) to appear empty on the client.

What's up with that?

---

### Post by jamesisin on 2013-09-15
Anybody?

---

### Post by jamesisin on 2013-09-17
Hello?

---

### Post by jamesisin on 2013-09-18
I must ask really challenging questions.

---

### Post by jamesisin on 2013-11-04
I circumnavigated this issue by using hard-links in lieu of soft-links and disabling wide links again.

---

