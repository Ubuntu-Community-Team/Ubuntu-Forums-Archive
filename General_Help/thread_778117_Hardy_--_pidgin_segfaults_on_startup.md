---
title: "Hardy -- pidgin segfaults on startup"
date: 2008-05-01
forum: General Help
---

### Post by kkinder on 2008-05-01
Here's the bottom of the strace:
```

open("/usr/lib/i486-linux-gnu/sse2/cmov/libsoftokn3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2/cmov", 0xbfb44c7c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/libsoftokn3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/sse2", 0xbfb44c7c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/cmov/libsoftokn3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/cmov", 0xbfb44c7c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/libsoftokn3.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
munmap(0xb4a19000, 90002)               = 0
open("/usr/lib/libpurple/libnssckbi.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libnssckbi.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/nss/libnssckbi.so", O_RDONLY) = 16
read(16, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360q\0"..., 512) = 512
fstat64(16, {st_mode=S_IFREG|0644, st_size=308096, ...}) = 0
mmap2(NULL, 306808, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 16, 0) = 0xb49e4000
mmap2(0xb4a25000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 16, 0x41) = 0xb4a25000
close(16)                               = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Process 8183 detached

```

---

