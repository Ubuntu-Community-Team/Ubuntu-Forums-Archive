---
title: "updatedb in uninterruptible wait state"
date: 2005-09-06
forum: General Help
---

### Post by nszabolcs on 2005-09-06
what can i do when a program is in D state?
```

nsz@ubuntu:~ $ ps -A -F -l | grep updatedb
4 D root     30806 30805  0  86  10 -   471 sync_p  4   0 07:37 ?        00:00:07 /usr/bin/updatedb
0 S nsz       4013  4861  0  76   0 -   738 pipe_w 600  0 10:51 pts/2    00:00:00 grep updatedb

```

I can't kill it.
Is there a way to get info about why is it stuck there ?

Edit: System Monitor screenshot
[[img]http://xs45.xs.to/pics/05362/updatedb_uninterruptible.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs45&d=05362&f=updatedb_uninterruptible.png)

---

### Post by frodon on 2005-09-06
[QUOTE=nszabolcs]what can i do when a program in D state?
```

nsz@ubuntu:~ $ ps -A -F -l | grep updatedb
4 D root     30806 30805  0  86  10 -   471 sync_p  4   0 07:37 ?        00:00:07 /usr/bin/updatedb
0 S nsz       4013  4861  0  76   0 -   738 pipe_w 600  0 10:51 pts/2    00:00:00 grep updatedb

```

I can't kill it.
Is there a way to get info about why is it stuck there ?[/QUOTE]You really can't kill it ? **sudo kill -9 30806 ** doesn't work ?

---

### Post by nszabolcs on 2005-09-06
[QUOTE=frodon]You really can't kill it ? **sudo kill -9 30806 ** doesn't work ?[/QUOTE]
nope

```

nsz@ubuntu:~ $ sudo kill -9 30806
nsz@ubuntu:~ $ ps -e u | grep updatedb
root     30806  0.0  0.0   1884     4 ?        DN   07:37   0:07 /usr/bin/updatedb
nsz       5085  0.0  0.1   2948   572 pts/2    R+   11:32   0:00 grep updatedb

```

---

### Post by martibs on 2006-02-04
Do you have an external hard drive? I experience the same problem, and in my case it is because of a FireWire hard drive.

---

### Post by fuelnatchos on 2008-06-30
try this:

kill -9 1234
strace -p 1234

(with 1234 being the PID)

It worked for me... the strace connecting to the process seems to get updatedb out of its sleep state, and then it gets the kill signal and dies...

---

