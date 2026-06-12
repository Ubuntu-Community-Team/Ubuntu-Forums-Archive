---
title: "[SOLVED] make search recurse ALWAYS"
date: 2008-02-12
forum: General Help
---

### Post by Izek on 2008-02-12
How do I get the search to recurse to subdirs and dirs? For example, if I search in the filesystem (root directory, ./) for blahblah.txt when blahblah.txt is in the usr folder, it comes up with the result from the usr dir. Currently, it'll show no results unless the file is in the directory you are searching.

---

### Post by geraldm on 2008-02-12
use the command find for recursive searches.
```

find ~/startdir -name "blahblah.txt" -print

```
If you still have a problem after reading the manpage for whatever command you are using, then post that command, and the reason for doubt or difficulty

Gerald

---

