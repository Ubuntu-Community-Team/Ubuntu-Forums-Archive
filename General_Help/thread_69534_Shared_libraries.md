---
title: "Shared libraries"
date: 2005-09-27
forum: General Help
---

### Post by mthaddon on 2005-09-27
This issue has come up as I'm trying to get started with QEMU. I'm hoping someone might know enough about Shared Libraries to help me out. I'm running the qemu-0.7.2-i386.tar.gz - Binary distribution for linux-i386.

If I run ldd /usr/local/bin/qemu I get:
```
linux-gate.so.1 =>  (0x00000000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x5557d000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x555a0000)
        libSDL-1.2.so.0 => not found
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x555b2000)
        libutil.so.1 => /lib32/tls/libutil.so.1 (0x555c1000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x555c4000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x55555000)

```

And, of course, the missing SDL library shows up if I try to actually run QEMU. However, if I run ldconfig -p | grep SDL I get:

```
libSDL_ttf-2.0.so.0 (libc6,x86-64) => /usr/lib/libSDL_ttf-2.0.so.0
        libSDL_sound-1.0.so.1 (libc6,x86-64) => /usr/lib/libSDL_sound-1.0.so.1
        libSDL_net-1.2.so.0 (libc6,x86-64) => /usr/lib/libSDL_net-1.2.so.0
        libSDL_mixer-1.2.so.0 (libc6,x86-64) => /usr/lib/libSDL_mixer-1.2.so.0
        libSDL_image-1.2.so.0 (libc6,x86-64) => /usr/lib/libSDL_image-1.2.so.0
        libSDL_gfx.so.0 (libc6,x86-64) => /usr/lib/libSDL_gfx.so.0
        libSDL_console.so.1 (libc6,x86-64) => /usr/lib/libSDL_console.so.1
        libSDL-1.2.so.0 (libc6,x86-64) => /usr/lib/libSDL-1.2.so.0

```

That last one is the very one it's complaining it can't find. Can anyone help out?

Thanks, Tom

---

