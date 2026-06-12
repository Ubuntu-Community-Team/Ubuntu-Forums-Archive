---
title: "How to search for files over a certain size with ubuntu"
date: 2019-01-30
forum: General Help
---

### Post by Tom_Carr on 2019-01-30
I am using ubuntu 18.04 and the file manager that comes with it.  In an older version the file manager would let me search for all files over a selected size, but I don't see that option in the current file manager.  How do I search for large files?

---

### Post by raleigh3 on 2019-01-30
In Mate Search Tool, select more options. Size is one of those options.

---

### Post by Holger_Gehrke on 2019-01-31
The command line tool can do this (and a lot more):
```
find ~ -size +1G
```
will  search in your home directory and it's subdirectories for files larger  than 1 Gibibyte. See the man page for details and explanations.

Holger

---

### Post by Tom_Carr on 2019-01-31
Thanks

---

