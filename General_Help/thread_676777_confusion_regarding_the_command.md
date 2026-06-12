---
title: "confusion regarding the command"
date: 2008-01-24
forum: General Help
---

### Post by alwar.sumit on 2008-01-24
what did the following command do:

rm -rf .*

---

### Post by scxtt on 2008-01-24
recursively (-r), forcibly (-f) deleted (rm) any "hidden" directory / file (.*) ...
```
:> touch .test1 .test2 test3; mkdir test4; mkdir .test5

:> ls -al
total 16
drwxr-xr-x  4 scxtt users 4096 Jan 24 05:22 .
drwxr-xr-x 44 scxtt scxtt 4096 Jan 24 05:21 ..
-rw-r--r--  1 scxtt users    0 Jan 24 05:22 .test1
-rw-r--r--  1 scxtt users    0 Jan 24 05:22 .test2
drwxr-xr-x  2 scxtt users 4096 Jan 24 05:22 .test5
-rw-r--r--  1 scxtt users    0 Jan 24 05:22 test3
drwxr-xr-x  2 scxtt users 4096 Jan 24 05:22 test4

:> rm -rf .*

:> ls -al
total 12
drwxr-xr-x  3 scxtt users 4096 Jan 24 05:22 .
drwxr-xr-x 44 scxtt scxtt 4096 Jan 24 05:21 ..
-rw-r--r--  1 scxtt users    0 Jan 24 05:22 test3
drwxr-xr-x  2 scxtt users 4096 Jan 24 05:22 test4
```

---

