---
title: "vpn program runs in edgy - but not feisty"
date: 2007-06-18
forum: General Help
---

### Post by bagpussnz on 2007-06-18
Hi,
I have a program (a checkpoint vpn - snx) that runs in edgy and previous ubuntus, but when I run it in Fiesty - I get,

snx
Segmentation fault (core dumped)

It happens on all Feisty installs.

ldd snx returns,

        linux-gate.so.1 =>  (0xffffe000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7dea000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7dd3000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7dc0000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7dbc000)
        libpam.so.0 => /lib/libpam.so.0 (0xb7db4000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7d9d000)
        libcpc++-libc6.1-2.so.3 => /usr/lib/libcpc++-libc6.1-2.so.3 (0xb7ce2000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7ba1000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b9e000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b99000)
        /lib/ld-linux.so.2 (0xb7ef0000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b72000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b65000)

Any ideas anyone?

Cheers,
Ian.

---

