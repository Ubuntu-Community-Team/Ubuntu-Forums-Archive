---
title: "help (again) with a script"
date: 2008-02-27
forum: General Help
---

### Post by jmvidalvia on 2008-02-27
I am extracting text from a file with cat and awk.
Once I have it, I get something like:
```
00058326
```
I need to insert this number into an e-mail subject, but I need to convert this chain from **00058326** to **58,326**, in order to make it readable.
Any Idea?
Thanks a lot!:)

---

### Post by spupy on 2008-02-27
To strip leading 0:
```
 echo $number | sed -e s/^0*//
```
But that doesn't insert the ",".

---

### Post by jmvidalvia on 2008-02-27
Thanks a lot!
:)

---

