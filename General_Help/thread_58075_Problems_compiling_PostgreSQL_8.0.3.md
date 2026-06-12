---
title: "Problems compiling PostgreSQL 8.0.3"
date: 2005-08-18
forum: General Help
---

### Post by DamnDirtyApe on 2005-08-18
Hi y'all,

I'm attempting to compile PostgreSQL 8.0.3 from source on a relatively fresh Hoary system, and I'm having some unexpected difficulties.  When I run the following command:

```
./configure --prefix=/opt/pg803
```

I get an error saying that the readline library cannot be found.  apt packages for both libreadline4 and libreadline5 are installed.  When I try this:

```
./configure --prefix=/opt/pg803 --without-readline
```

I get an error that zlib cannot be found.  Can anyone give me a hand with this?

---

### Post by krusbjorn on 2005-08-18
Did you install libreadline4-dev and libreadline5-dev?

Edit: (or zlib1g and zlib1g-dev for that matter?)

---

### Post by DamnDirtyApe on 2005-08-18
That did it.  Thanks!

---

### Post by adaum on 2006-01-27
it worked with **zlib1g-dev**

---

