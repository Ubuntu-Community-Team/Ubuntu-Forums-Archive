---
title: "Can't see hebrew files"
date: 2006-09-03
forum: General Help
---

### Post by kroiz on 2006-09-03
when mounting my windows partition, files with hebrew names are not displayed. not from the command line nor from any gui.
any way to fix that?

---

### Post by mssever on 2006-09-03
Do you use nls=utf8 in your mount options? I believe that your /etc/fstab should contain nls=utf8 in the options column.

---

### Post by kroiz on 2006-09-04
That does it.
Thanks alot.

---

