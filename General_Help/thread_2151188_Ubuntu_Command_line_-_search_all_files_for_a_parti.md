---
title: "Ubuntu Command line - search all files for a particular string"
date: 2013-06-03
forum: General Help
---

### Post by lovatto on 2013-06-03
Hello all

Using the terminal I am trying to search all files for a particular string

This is my attempt

find . -iname "*" -print0 | xargs -0 cat | grep "208.122.23.2" | >> ~/Documents/searchres

Now this works BUT it is missing one quite important detail, and that is the filename

How would I include this in my output please?

---

### Post by ahallubuntu on 2013-06-03
How about:

```
find . -exec grep -Hn 208.122.23.2 {} \;
```

---

### Post by HiImTye on 2013-06-04
```
grep '208.122.23.2' *
```

edit: if you want line numbers```
grep -n '208.122.23.2' *
```

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by markbl on 2013-06-04
```

grep -rF 208.122.23.2

```
is the answer.

---

