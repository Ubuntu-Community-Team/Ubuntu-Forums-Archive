---
title: "/dev/pts/tty0.. ???whats thihs?"
date: 2008-06-01
forum: General Help
---

### Post by karan mangat on 2008-06-01
whenever i open a new terminal, a file is created at /dev/pts/,
named tty(n-1), where n is nth terminal.
it is definitely not a text file.
i cannot even see its properties.
what are these files?

---

### Post by prshah on 2008-06-01
> **karan mangat said:**
> whenever i open a new terminal, a file is created at /dev/pts/,
named tty(n-1), where n is nth terminal.
it is definitely not a text file.
i cannot even see its properties.
what are these files?

This is a character device pseudo terminal slave (hence pts) file. It's not a real file; it's a representation of a emulated terminal. Similar to /proc/kcore which is a virtual file representing your RAM memory.
```
man pts
``` will give you (lots) more information.

---

### Post by Ramses de Norre on 2008-06-01
This is the unix philosophy, everything is a file.

---

### Post by karan mangat on 2008-06-01
can i use it for any of my benifits?

---

### Post by Joeb454 on 2008-06-01
I don't think you'd need to, or have any benefit from it :)

---

