---
title: "Evolution segfaults in LTSP thin clients"
date: 2017-06-06
forum: General Help
---

### Post by v4169sgr on 2017-06-06
i386 variant of ubuntu 16.04.02 running LTSP

User attempting to run Evolution from the client. Evolution crashes out with a segfault.

Has this been seen before? If so, what can be done about it ?

Thanks :)

---

### Post by v4169sgr on 2017-06-07
Additional information: running under gdb on the thin client shows:

```

(gdb) run
Starting program: /usr/bin/evolution 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1".
[New Thread 0xb00efb40 (LWP 25812)]
[New Thread 0xaf6ffb40 (LWP 25813)]

Thread 1 "evolution" received signal SIGSEGV, Segmentation fault.
0xb7fe3d9b in check_match (undef_name=undef_name@entry=0xb3308ad1 "mincore", 
    ref=ref@entry=0x0, version=version@entry=0x0, flags=7, type_class=0, 
    sym=0xb32f91cc, symidx=163, strtab=0xb32f96cc "", map=0xb330a000, 
    versioned_sym=0xbf8000ac, num_versions=0xbf8000a8) at dl-lookup.c:110
110	dl-lookup.c: No such file or directory.


```

The same command run on the server as the same user in the same desktop environment completes successfully

---

