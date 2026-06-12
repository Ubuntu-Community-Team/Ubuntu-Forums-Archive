---
title: "Unexpected output from command ls -1"
date: 2012-12-02
forum: General Help
---

### Post by 53om on 2012-12-02
Hello!

I'm pretty new to Linux and using the command line.

I'm using Ubuntu 12.04

When I try to view the permission for a directory using ls -1, I just get a listing of the files and subdirectories in the folder. I thought ls -1 would give you output that might look something like this:

-rw-rw-r-- 1 me   me   1097374 Sep 26 18:48 some_file

instead I get something like this:

Desktop
Downloads
Music
Pictures
etc
etc
etc

What am I doing wrong?

Thanks!

---

### Post by Vaphell on 2012-12-02
```
ls -l
```

always check commands by using them with *--help*. Most show list of available options

```
$ ls --help

-l                         use a long listing format

-1                         list one file per line
```

---

### Post by JKyleOKC on 2012-12-02
To get what you want, the "-l" option should be a lower-case L, not the numeral 1. Many fonts don't make the difference obvious visually.

---

