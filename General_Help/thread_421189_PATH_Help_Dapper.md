---
title: "PATH Help Dapper"
date: 2007-04-24
forum: General Help
---

### Post by Otto-C on 2007-04-24
Where do I add to the startup PATH.

tia
Otto-c

---

### Post by Compyx on 2007-04-24
Edit the file .bashrc in your home directory, and add any paths by putting a line like this at the end:
```

export PATH=$PATH:<new path(s)>

```

For example, here's what I have:
```

export PATH=$PATH:/home/compyx/scripts

```
this will allow me to run some self-written scripts I have.

You separate multiple paths with a colon ':'.

---

