---
title: "[SOLVED] NOOB:  adding a directory to the path environment variable"
date: 2008-03-28
forum: General Help
---

### Post by notatoad on 2008-03-28
i'm setting up glassfish ee server, and it tells me to "Add the install-dir/bin/ directory to the PATH environment variable."  how do i do that?

---

### Post by dcstar on 2008-03-28
> **notatoad said:**
> i'm setting up glassfish ee server, and it tells me to "Add the install-dir/bin/ directory to the PATH environment variable."  how do i do that?

In a Gnome terminal:

```
gksudo gedit /etc/environment
```

---

### Post by pointone on 2008-03-29
For a temporary change, all that is needed is a simple:

```
PATH=$PATH:/directory
```

---

