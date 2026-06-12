---
title: "install problems with personal acountz 6"
date: 2007-03-31
forum: General Help
---

### Post by gavinjb on 2007-03-31
Hi,

I am trying to install the Linux version of Personal Accountz 6, but when installing I get the following error

```

grep: error while loading shared libraries: libc.so.6: cannot open
shared object file: No such file or directory
/usr/lib/jvm/java-6-sun/jre/bin/java: error while loading shared
libraries: libpthread.so.0: cannot open shared object file: No such file
or directory

```

I searched for libc.so.6 and found it in /lib

I ran ran ls libc -ls and it reported that it was a shortcut pointing to libc-2.4.so also in /lib directory

So I ran ldd libc-2.4.so and I get

/lib/ld-linux.so.2 (0xb7f34000)
linux-gate.so.1 =>  (0xffffe000)

I just tried running ls ld-linux.so.2 -ls and I get ld-2.4.so which does not exist and is not in the repository any ideas or am I looking in completely the wrong place?


Gavin,

---

