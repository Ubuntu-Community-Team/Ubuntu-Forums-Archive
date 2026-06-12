---
title: "How do you install Python 3.3.2"
date: 2013-07-02
forum: General Help
---

### Post by demonic_crow on 2013-07-02
I'm running Ubuntu 12.04. I'm needing to install Python 3.3.2 on my laptop for a class. I went to python.org and downloaded the tarbell. When I run ./configure everything seem to be fine. After I type **make  **I run into a problem.

```
gcc -pthread -c -Wno-unused-result -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes     -I. -IInclude -I./Include    -DPy_BUILD_CORE \
        -DABIFLAGS='"m"' \
        -o Python/sysmodule.o ./Python/sysmodule.c
gcc -pthread -c -Wno-unused-result -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes     -I. -IInclude -I./Include    -DPy_BUILD_CORE \
        -DSOABI='"cpython-33m"' \
        -o Python/dynload_shlib.o ./Python/dynload_shlib.c
gcc -pthread -c -Wno-unused-result -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes     -I. -IInclude -I./Include    -DPy_BUILD_CORE -o Modules/config.o Modules/config.c
gcc -pthread -c -Wno-unused-result -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes     -I. -IInclude -I./Include    -DPy_BUILD_CORE -DPYTHONPATH='":plat-linux"' \
        -DPREFIX='"/usr/local"' \
        -DEXEC_PREFIX='"/usr/local"' \
        -DVERSION='"3.3"' \
        -DVPATH='""' \
        -o Modules/getpath.o ./Modules/getpath.c
gcc -pthread -c -Wno-unused-result -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes     -I. -IInclude -I./Include    -DPy_BUILD_CORE \
          -DHGVERSION="\"`LC_ALL=C `\"" \
          -DHGTAG="\"`LC_ALL=C `\"" \
          -DHGBRANCH="\"`LC_ALL=C `\"" \
          -o Modules/getbuildinfo.o ./Modules/getbuildinfo.c
rm -f libpython3.3m.a
ar rc libpython3.3m.a Modules/getbuildinfo.o
*** buffer overflow detected ***: ar terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x37)[0x2add10ba1817]
/lib/x86_64-linux-gnu/libc.so.6(+0x109710)[0x2add10ba0710]
/lib/x86_64-linux-gnu/libc.so.6(+0x108b79)[0x2add10b9fb79]
/lib/x86_64-linux-gnu/libc.so.6(_IO_default_xsputn+0xdd)[0x2add10b1313d]
/lib/x86_64-linux-gnu/libc.so.6(_IO_padn+0xf8)[0x2add10b07558]
/lib/x86_64-linux-gnu/libc.so.6(_IO_vfprintf+0x2334)[0x2add10ae1cf4]
/lib/x86_64-linux-gnu/libc.so.6(__vsprintf_chk+0x94)[0x2add10b9fc14]
/lib/x86_64-linux-gnu/libc.so.6(__sprintf_chk+0x7d)[0x2add10b9fb5d]
ar[0x409a84]
ar[0x407ce1]
ar[0x40a32d]
ar[0x40d7b7]
ar[0x4047ef]
ar[0x404cad]
ar[0x405642]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x2add10ab876d]
ar[0x401ef9]
======= Memory map: ========
00400000-0048b000 r-xp 00000000 08:05 5384338                            /usr/local/bin/ar
0068b000-0068c000 r--p 0008b000 08:05 5384338                            /usr/local/bin/ar
0068c000-0068d000 rw-p 0008c000 08:05 5384338                            /usr/local/bin/ar
0068d000-0068f000 rw-p 00000000 00:00 0 
00cb6000-00cd7000 rw-p 00000000 00:00 0                                  [heap]
2add10872000-2add10894000 r-xp 00000000 08:05 7345354                    /lib/x86_64-linux-gnu/ld-2.15.so
2add10894000-2add10896000 rw-p 00000000 00:00 0 
2add10a94000-2add10a95000 r--p 00022000 08:05 7345354                    /lib/x86_64-linux-gnu/ld-2.15.so
2add10a95000-2add10a97000 rw-p 00023000 08:05 7345354                    /lib/x86_64-linux-gnu/ld-2.15.so
2add10a97000-2add10c4c000 r-xp 00000000 08:05 7345199                    /lib/x86_64-linux-gnu/libc-2.15.so
2add10c4c000-2add10e4b000 ---p 001b5000 08:05 7345199                    /lib/x86_64-linux-gnu/libc-2.15.so
2add10e4b000-2add10e4f000 r--p 001b4000 08:05 7345199                    /lib/x86_64-linux-gnu/libc-2.15.so
2add10e4f000-2add10e51000 rw-p 001b8000 08:05 7345199                    /lib/x86_64-linux-gnu/libc-2.15.so
2add10e51000-2add10e58000 rw-p 00000000 00:00 0 
2add10e58000-2add11121000 r--p 00000000 08:05 4996486                    /usr/lib/locale/locale-archive
2add11121000-2add11128000 r--s 00000000 08:05 7345443                    /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
2add11128000-2add1112c000 rw-p 00000000 00:00 0 
2add1114f000-2add11164000 r-xp 00000000 08:05 7340182                    /lib/x86_64-linux-gnu/libgcc_s.so.1
2add11164000-2add11363000 ---p 00015000 08:05 7340182                    /lib/x86_64-linux-gnu/libgcc_s.so.1
2add11363000-2add11364000 r--p 00014000 08:05 7340182                    /lib/x86_64-linux-gnu/libgcc_s.so.1
2add11364000-2add11365000 rw-p 00015000 08:05 7340182                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fff8e2ae000-7fff8e2cf000 rw-p 00000000 00:00 0                          [stack]
7fff8e3b4000-7fff8e3b5000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
make: *** [libpython3.3m.a] Aborted (core dumped)
make: *** Deleting file `libpython3.3m.a'
```

---

### Post by dino99 on 2013-07-02
you can download these deb packages (ready to use) into an empty folder, from : [https://launchpad.net/ubuntu/+source/python3.3](https://launchpad.net/ubuntu/+source/python3.3)

then from that folder, run: sudo dpkg -i thepackageyouneed2install

---

### Post by demonic_crow on 2013-07-02
I downloaded all the deb packages. I ran through each one and none of them would installed.

---

### Post by sanderj on 2013-07-02
> **demonic_crow said:**
> I'm running Ubuntu 12.04. I'm needing to install Python 3.3.2 on my laptop for a class. 

Python 3.3.2? For a class? Really? Why?

I would understand "You need python3 for this" or maybe "you need python 3.3 for this", but "python 3.3.2" .... ?

---

