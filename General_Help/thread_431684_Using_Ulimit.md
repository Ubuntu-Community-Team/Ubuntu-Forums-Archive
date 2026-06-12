---
title: "Using Ulimit"
date: 2007-05-03
forum: General Help
---

### Post by rnichols430 on 2007-05-03
If I try to use ulimit -n 8192, I get bash: ulimit: open files: cannot modify limit: Operation not permitted
if I try to use sudo ulimit -n 8192.  I get Unknown command..  How do I run the ulimit?

Thanks,
Ryan Nichols

---

### Post by lloyd_b on 2007-05-03
From the bash man page:
```
 -l     The maximum size that may be locked into memory
 -m     The maximum resident set size
 -n     The maximum number of open file descriptors [B](most systems 
         do not allow this value to be set)[/B]
 -p     The pipe size in 512-byte blocks (this may not be set)
 -q     The maximum number of bytes in POSIX message queues
```
Checking some other man pages, it appears that Linux does not allow that value to be set.

Lloyd B.

---

### Post by rnichols430 on 2007-05-03
Ah, ok.. I was trying this to increase from the 1024 to someting higher for Ktorrent.. Someone had suggested to use this command, but provided no way to do it, so i researched it and figured that part out.. But it wouldnt take..

Thanks,
RyanNichols

---

