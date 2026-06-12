---
title: "Find all filenames containing non-ascii characters."
date: 2008-05-24
forum: General Help
---

### Post by keeler1 on 2008-05-24
How could I find all filenames in a directory (or in the subdirectory tree of that directory) that have non-ascii characters in them.  I was thinking of using grep or find but I would not know how to specify that a non-ascii character is contained in the name.  Other than searching every subdirectory manually which would take forever since it contains over a hundred subdirectories which then contain subdirectories, or writing some code myself is there any way to find this?

---

### Post by Iowan on 2008-05-24
There's **awk** (or **mawk**).  I briefly looked at **man awk**.  Regular expressions should be able to handle the requirements... but I don't have the experience to givve exact sequence.

---

### Post by HalPomeranz on 2008-05-24
I don't have any files sitting around with non-ASCII characters in their names that I can test with, but the following ought to work:

```
find /tmp | perl -ne 'print if /[^[:ascii:]]/'
```

Replace /tmp with the name of the directory you want to search through.

---

