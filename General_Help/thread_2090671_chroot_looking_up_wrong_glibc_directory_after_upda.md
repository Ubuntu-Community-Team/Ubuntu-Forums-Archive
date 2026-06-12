---
title: "chroot looking up wrong glibc directory after update to 12.10"
date: 2012-12-03
forum: General Help
---

### Post by testvogel on 2012-12-03
Hello,

I've updated my ubuntu server installation to 12.10. The update process was successfull, but I'm unable to use "chroot" now.

```

root@my:/# chroot /srv
/bin/bash: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by /bin/bash)
/bin/bash: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.15' not found (required by /bin/bash)
```If I try use

```

chroot /srv anyDir/in/srv

```I get a segmentation fault.

```

root@my:/# ldd -v /bin/bash 
        linux-gate.so.1 =>  (0xb7754000)
        libtinfo.so.5 => /lib/i386-linux-gnu/libtinfo.so.5 (0xb7724000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb771f000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7574000)
        /lib/ld-linux.so.2 (0xb7755000)

        Version information:
        /bin/bash:
                libdl.so.2 (GLIBC_2.1) => /lib/i386-linux-gnu/libdl.so.2
                libdl.so.2 (GLIBC_2.0) => /lib/i386-linux-gnu/libdl.so.2
                libc.so.6 (GLIBC_2.11) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1.1) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.8) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.15) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.2) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.4) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.3.4) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.0) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.3) => /lib/i386-linux-gnu/libc.so.6
        /lib/i386-linux-gnu/libtinfo.so.5:
                libc.so.6 (GLIBC_2.3) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.2) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1.3) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.4) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.3.4) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.0) => /lib/i386-linux-gnu/libc.so.6
        /lib/i386-linux-gnu/libdl.so.2:
                ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
                libc.so.6 (GLIBC_PRIVATE) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1.3) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.0) => /lib/i386-linux-gnu/libc.so.6
        /lib/i386-linux-gnu/libc.so.6:
                ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
                ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
                ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2

``````

root@my:/# ldd -v $(which chroot)
        linux-gate.so.1 =>  (0xb7773000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb75b8000)
        /lib/ld-linux.so.2 (0xb7774000)

        Version information:
        /usr/sbin/chroot:
                libc.so.6 (GLIBC_2.3) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.3.4) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1.3) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.2) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.4) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.1) => /lib/i386-linux-gnu/libc.so.6
                libc.so.6 (GLIBC_2.0) => /lib/i386-linux-gnu/libc.so.6
        /lib/i386-linux-gnu/libc.so.6:
                ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
                ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
                ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2

```The directory "/lib/tls/i686/cmov/libc.so.6" doesnt exist anymore and I guess the lookup folder of chroot for GLIBC_2.11 and GLIBC_2.15 has to be changed. Due to the fact I'm not very good in ubuntu I don't know where I can change these paths.
Some help would be appreciated.

Greets
testvogel

---

