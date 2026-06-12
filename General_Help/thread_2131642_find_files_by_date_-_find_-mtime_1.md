---
title: "find files by date - find -mtime 1"
date: 2013-04-02
forum: General Help
---

### Post by sohlinux on 2013-04-02
How can I find files which were modified in the past week or between certain dates?

I can use the following ```
find /path -mtime 1
``` but that only shows the last day

thanks

---

### Post by steeldriver on 2013-04-02
you can use multiple mtime predicates e.g.

```
$ find . -mtime +14 -mtime -28 -ls
```

or for absolute dates try newerXY e.g.

```
$ find . -newermt '2013-03-11' ! -newermt '2013-03-14' -ls
```

---

### Post by sohlinux on 2013-04-02
perfect! thanks

---

