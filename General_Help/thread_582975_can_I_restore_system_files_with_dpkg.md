---
title: "can I restore system files with dpkg?"
date: 2007-10-20
forum: General Help
---

### Post by baritono on 2007-10-20
Hi, all
I removed some header files under /usr/include by mistake and want to get them back. I wonder since dpkg keeps a database of all installed files, maybe I can do some queries, find out which installed packages have files under /usr/include and reinstall them all. Is that possible? How can  I do it efficiently?
Thanks!

---

### Post by chrisccoulson on 2007-10-20
If you know which files you removed, you could try:
```
grep /path/to/deleted/file /var/lib/dpkg/info/*.list
```

should list the packages that those files were in.

---

### Post by baritono on 2007-10-20
Thanks for your help! I've got the work done :)

---

### Post by chrisccoulson on 2007-10-20
No probs!

---

