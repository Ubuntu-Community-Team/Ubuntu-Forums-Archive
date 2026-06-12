---
title: "Mass rename: remove prefix"
date: 2013-03-11
forum: General Help
---

### Post by hojjat on 2013-03-11
I have a bunch of files which are named like this:

01_asdsdsdsad
02_131l2kj2jk
03_a--00asd90
...

You get the idea. I want to use "rename" or a bash script to remove the two digits and the underscore from the beginning of the file. It is always three characters long. Any advice?

---

### Post by steeldriver on 2013-03-11
you could try

```
rename -n -v 's/^[0-9]{2}_//' *
```

if it appears to be matching correctly then remove the '-n' (dry run) to make it actually modify the names

---

### Post by hojjat on 2013-03-11
Thanks!

---

