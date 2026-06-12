---
title: "Eclipse hungs @ exit"
date: 2006-10-12
forum: General Help
---

### Post by szundi on 2006-10-12
Hello, my eclipse java process started to hang at exit. There was no similar errors with dapper. What can be the cause?

```
18792 ?        S      0:00 /home/szundi/java/eclipse/eclipse
18793 ?        Sl     0:14 /usr/bin/java -Xms40m -Xmx256m -jar /home/szundi/java
18965 pts/2    R+     0:00 ps ax
szundi@galactica:~$ strace -p 18793
Process 18793 attached - interrupt to quit
futex(0x839c7fc, FUTEX_WAIT, 193, NULL <unfinished ...>
Process 18793 detached
szundi@galactica:~$ 

```

What can be the solution? Dapper didn't have this problem.

Thanks
Szundi

---

