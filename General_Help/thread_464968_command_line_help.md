---
title: "command line help"
date: 2007-06-05
forum: General Help
---

### Post by carverj on 2007-06-05
Hi there all,
                      My question for today....
 How might I display a listing of all the symbolic links in a directory, including relative links? And what is a relative link?? 
  I was thinking find or ls ??
Ta for your help!!
:)

---

### Post by stylishpants on 2007-06-05
To show only links in the current working directory, use this:
```
find . -maxdepth 1 -type l
```

To show links in all subdirs as well, get rid of the 'maxdepth' option:
```
find . -type l
```

A relative link is a link to a location defined relative to the current directory, like '../' or 'sub/dir'.

An absolute link is defined relative to the root directory.  It always starts with a slash.

Examples:
```

fraser@ged:/usr/local/bin$ ls -l | grep ^l

### ABSOLUTE LINKS
lrwxrwxrwx 1 root   root         32 2006-10-29 09:32 align -> /usr/local/src/align-1.7.0/align
lrwxrwxrwx 1 root   root          9 2006-10-29 09:32 ffmpeg -> /dev/null
lrwxrwxrwx 1 root   root         16 2006-10-29 09:32 gcc -> /usr/bin/gcc-3.4
lrwxrwxrwx 1 root   root         26 2006-10-29 09:32 maple -> /usr/local/maple/bin/maple
lrwxrwxrwx 1 root   root         27 2006-10-29 09:32 xmaple -> /usr/local/maple/bin/xmaple

### RELATIVE LINKS
lrwxrwxrwx 1 root   root         13 2006-10-29 09:32 autostop -> ./autostop.rb
lrwxrwxrwx 1 root   root         29 2006-10-29 09:32 exfalso -> ../share/quodlibet/exfalso.py
lrwxrwxrwx 1 root   root         31 2006-10-29 09:32 quodlibet -> ../share/quodlibet/quodlibet.py


```

---

