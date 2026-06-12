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

### Post by szundi on 2006-10-12
Ah, and my java version is sun 1.5.0_08, _09 is the same.
My edgy is upgraded from dapper with aptitude.

---

### Post by eitan on 2006-10-22
i had downloaded eclipse 3.2.1 (latest) on edgy and had the same problem you mention.

i ended up using the verion of eclipse (3.1) in the ubuntu repositories, which seems to work.  my god is it slow!

---

### Post by eitan on 2006-10-31
by the way, i recently upgraded eclipse to v3.2.1 via the repositories and this version works.  still god slow.
intellij idea is my ide of choice for java development, and it's faster than eclipse.

---

