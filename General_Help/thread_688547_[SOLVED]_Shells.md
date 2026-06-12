---
title: "[SOLVED] Shells"
date: 2008-02-05
forum: General Help
---

### Post by upthelum on 2008-02-05
How do i find out which shell i am using, anyone please?

---

### Post by Fraktyl on 2008-02-05
Check /etc/passwd.  The last field is the shell you're using.

```

grep [yourusername] /etc/passwd

```

---

### Post by upthelum on 2008-02-05
It's bash. Nice one thanks...

---

### Post by bodhi.zazen on 2008-02-05
```
echo $SHELL
``` will show your default shell. You should know if you changed shells ;)

---

