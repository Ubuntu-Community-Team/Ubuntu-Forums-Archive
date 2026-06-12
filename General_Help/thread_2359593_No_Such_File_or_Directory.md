---
title: "No Such File or Directory"
date: 2017-04-25
forum: General Help
---

### Post by favetella on 2017-04-25
Same issue. Any solution, please?

> 
$ chmod +x adb run.sh$ sh run.sh
run.sh: 2: run.sh: ./adb: not found


run.sh: 7: run.sh: ./adb: not found

$ ls -la
totale 1224
drwxrwxr-x 2 manolo manolo    4096 gen 30  2013 .
drwxr-xr-x 4 manolo manolo    4096 apr 25 19:29 ..
-rwxrwxr-x 1 manolo manolo 1226659 feb  1  2013 adb
-rw-r--r-- 1 manolo manolo     102 gen 30  2013 README
-rw-r--r-- 1 manolo manolo     185 gen 30  2013 ._README
-rwxr-xr-x 1 manolo manolo     185 gen 31  2013 ._run.sh
-rwxr-xr-x 1 manolo manolo     351 gen 31  2013 run.sh


---

### Post by QIII on 2017-04-25
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2353442](https://ubuntuforums.org/showthread.php?t=2353442)

Hello!

It is best to start your own thread rather than to hijack the thread of another user.  You are not likely to get help that way ... and we consider it rude to the other user.

Thanks.

---

### Post by spjackson on 2017-04-25
Please post the output from
```

file adb
ldd adb
uname -a

```

---

### Post by TheFu on 2017-04-25
If you typed exactly this ```

chmod +x adb run.sh$ sh run.sh
```
on a single command line, then the problem is clear. You should type:
```
sh ./run.sh
```

However, there is an error on line 7 of the run.sh script.  What does the top 10 lines of that file look like?

I suspect it is a PATH issue, but cannot tell.  Would love to see the top 10 lines (**head -n 10 ./run.sh** and **pwd** output.

---

