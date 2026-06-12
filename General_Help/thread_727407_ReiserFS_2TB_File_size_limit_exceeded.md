---
title: "ReiserFS 2TB File size limit exceeded"
date: 2008-03-17
forum: General Help
---

### Post by Vadir on 2008-03-17
```
File size limit exceeded (core dumped)
```
Running 7.10 Linux server 2.6.22-14-server #1 SMP Tue Feb 12 03:10:53 UTC 2008 x86_64 GNU/Linux

I am unable to create a file greater than 2199023251456 bytes (2TB)
I am running ReiserFS and it should support a file size of 8TB.

/etc/security/limits.conf is completely commented out

```
$ ulimit -a
core file size          (blocks, -c) unlimited
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 16375
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 16375
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

---

### Post by Vadir on 2008-03-18
bump

---

### Post by Vadir on 2008-03-19
bump

---

