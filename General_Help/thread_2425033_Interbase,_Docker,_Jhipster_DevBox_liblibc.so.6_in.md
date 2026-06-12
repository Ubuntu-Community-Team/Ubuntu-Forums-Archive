---
title: "Interbase, Docker, Jhipster DevBox: /lib/libc.so.6: invalid ELF header"
date: 2019-08-19
forum: General Help
---

### Post by furiousgraffiti on 2019-08-19
Hi, I use JHipster DevBox which is based on Xubuntu and I'm trying to run Interbase's server inside Docker's container

```

dev-interbase     | /opt/interbase/bin/ibmgr.bin: error while loading shared libraries: /lib/libc.so.6: invalid ELF header
dev-interbase     | /opt/interbase/bin/ibmgr.bin: error while loading shared libraries: /lib/libc.so.6: invalid ELF header
dev-interbase     | Wait until InterBase server is started
dev-interbase     | 
dev-interbase     | .
dev-interbase     | .
dev-interbase     | .

```
The problem is, my server never starts and displays nothing but dots......

Here's content of my /lib.. (without unimportant files in this case replaced with (...))
```

&#10140;  /lib ls -all
(...)
drwxr-xr-x  2 root root  4096 Aug 12 15:21 i386-linux-gnu
(...)
lrwxrwxrwx  1 root root    32 Aug 19 12:50 libc.so.6 -> /lib/i386-linux-gnu/libc-2.27.so
(...)
drwxr-xr-x  5 root root 12288 Aug 12 15:21 x86_64-linux-gnu

```

..and /lib64 folders
```

&#10140;  /lib ls /lib64 -all
(...)
lrwxrwxrwx  1 root root   31 Aug 12 16:35 libc.so.6 -> /lib/x86_64-linux-gnu/libc.so.6

```

I thought it will work if I add symlink inside /lib named libc.so.6 that  points on libc-2.27.so but it actually doesn't and I'm out of ideas despite  reinstalling glibc but.. I hope there's a simpler solution to repair that, help me, please :/

Thanks in advance

---

### Post by furiousgraffiti on 2019-08-19
Update!

I removed and downloaded Interbase's image again and it works now ^^

I also figured out that Docker uses its own libraries so I couldn't help in the way I tried

---

