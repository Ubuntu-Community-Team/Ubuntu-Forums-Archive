---
title: "Wine's libraries loaded above 2G (-&gt; crash)"
date: 2005-10-19
forum: General Help
---

### Post by meastp on 2005-10-19
Hi!

I tried to run RA2 the other day, and it crashed. Vitamin from the #winehq helped me, and said:


> In windows world no binaries could be loaded above 2G mark (0x7fffffff)
And you have bunch of them loaded there :-(
[...]
Wine should not have any libraries loaded above 2G mark

Is there any way to fix this?

Part of debug that vitamin said was relevant. I'll post the complete text if requested:

```

ELF     0x7ff0b000-80000000     Deferred        libwine_unicode.so.1
ELF     0xb7de1000-b7de3000     Deferred        libnvidia-tls.so.1
ELF     0xb7de3000-b7de6000     Deferred        libxau.so.6
ELF     0xb7de8000-b7deb000     Deferred        libdl.so.2
ELF     0xb7deb000-b7f19000     Deferred        libc.so.6
ELF     0xb7f19000-b7f2b000     Deferred        libpthread.so.0
ELF     0xb7f2b000-b7f44000     Deferred        libwine.so.1
ELF     0xb7f45000-b7f4e000     Deferred        libnss_nis.so.2
ELF     0xb7f53000-b7f69000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a (D) C:\RA2\game.exe
        00000010    2
        0000000e    0
        0000000d   15 <==
        0000000c    0
        0000000b    0
00000008
        00000009    0
WineDbg terminated on pid 0xa
meastp@ubuntu:~/.wine/drive_c/RA2$
```

---

