---
title: "Gimp crashing in 24.04 LTS"
date: 2024-04-30
forum: General Help
---

### Post by hrsetrdr on 2024-04-30
Last week Gimp worked normal, was running 22.04 LTS.  After installing 2**4**.04 LTS Gimp is seg-faulting.   I'm not good at analysing crash messages, what would this indicate?

```
```

GNU Image Manipulation Program version 2.10.36
git-describe: GIMP_2_10_36
Build: unknown rev 0 for linux
# C compiler #
	Using built-in specs.
	COLLECT_GCC=gcc
	COLLECT_LTO_WRAPPER=/usr/libexec/gcc/x86_64-linux-gnu/13/lto-wrapper
	OFFLOAD_TARGET_NAMES=nvptx-none:amdgcn-amdhsa
	OFFLOAD_TARGET_DEFAULT=1
	Target: x86_64-linux-gnu
	Configured with: ../src/configure -v --with-pkgversion='Ubuntu 13.2.0-23ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-13/README.Bugs --enable-languages=c,ada,c++,go,d,fortran,objc,obj-c++,m2 --prefix=/usr --with-gcc-major-version-only --program-suffix=-13 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/libexec --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-libstdcxx-backtrace --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --enable-default-pie --with-system-zlib --enable-libphobos-checking=release --with-target-system-zlib=auto --enable-objc-gc=auto --enable-multiarch --disable-werror --enable-cet --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none=/build/gcc-13-OiuXZC/gcc-13-13.2.0/debian/tmp-nvptx/usr,amdgcn-amdhsa=/build/gcc-13-OiuXZC/gcc-13-13.2.0/debian/tmp-gcn/usr --enable-offload-defaulted --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
	Thread model: posix
	Supported LTO compression algorithms: zlib zstd
	gcc version 13.2.0 (Ubuntu 13.2.0-23ubuntu3) 

# Libraries #
using babl version 0.1.108 (compiled against version 0.1.108)
using GEGL version 0.4.48 (compiled against version 0.4.48)
using GLib version 2.80.0 (compiled against version 2.80.0)
using GdkPixbuf version 2.42.10 (compiled against version 2.42.10)
using GTK+ version 2.24.33 (compiled against version 2.24.33)
using Pango version 1.52.1 (compiled against version 1.52.1)
using Fontconfig version 2.15.0 (compiled against version 2.15.0)
using Cairo version 1.18.0 (compiled against version 1.18.0)

```
> fatal error: Segmentation fault

Stack trace:
```

# Stack traces obtained from PID 8144 - Thread 8144 #


This GDB supports auto-downloading debuginfo from the following URLs:
  <https://debuginfod.ubuntu.com>
Enable debuginfod for this session? (y or [n]) [answered N; input not from terminal]
Debuginfod has been disabled.
To make this setting permanent, add 'set debuginfod enabled off' to .gdbinit.
[New LWP 8204]
[New LWP 8203]
[New LWP 8195]
[New LWP 8166]
[New LWP 8163]
[New LWP 8162]
[New LWP 8160]
[New LWP 8159]
[New LWP 8158]
[New LWP 8157]
[New LWP 8156]
[New LWP 8155]
[New LWP 8154]
[New LWP 8153]
[New LWP 8152]
[New LWP 8151]
[New LWP 8150]
[New LWP 8149]
[New LWP 8148]
[New LWP 8147]
[New LWP 8146]
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
0x000073b000f1ba9a in __GI___libc_read (nbytes=256, buf=0x7ffeeabb6570, fd=15) at ../sysdeps/unix/sysv/linux/read.c:26
  Id   Target Id                                         Frame 
* 1    Thread 0x73b000501640 (LWP 8144) "gimp-2.10"      0x000073b000f1ba9a in __GI___libc_read (nbytes=256, buf=0x7ffeeabb6570, fd=15) at ../sysdeps/unix/sysv/linux/read.c:26
  2    Thread 0x73afc8c006c0 (LWP 8204) "pool-gimp-2.10" syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  3    Thread 0x73afe90006c0 (LWP 8203) "paint"          syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  4    Thread 0x73afd6a006c0 (LWP 8195) "swap writer"    syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  5    Thread 0x73afd60006c0 (LWP 8166) "gimp-2.10"      syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  6    Thread 0x73afd74006c0 (LWP 8163) "gimp-2.10"      syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  7    Thread 0x73afd7e006c0 (LWP 8162) "async"          syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  8    Thread 0x73afe9a006c0 (LWP 8160) "gdbus"          0x000073b000f1b4cd in __GI___poll (fds=0x73afa4000b90, nfds=2, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
  9    Thread 0x73afea4006c0 (LWP 8159) "dconf worker"   0x000073b000f1b4cd in __GI___poll (fds=0x73afa8000b90, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
  10   Thread 0x73afeae006c0 (LWP 8158) "gmain"          0x000073b000f1b4cd in __GI___poll (fds=0x6289cc0933c0, nfds=2, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
  11   Thread 0x73afeb8006c0 (LWP 8157) "pool-spawner"   syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  12   Thread 0x73aff4c006c0 (LWP 8156) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  13   Thread 0x73aff56006c0 (LWP 8155) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  14   Thread 0x73aff60006c0 (LWP 8154) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  15   Thread 0x73aff6a006c0 (LWP 8153) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  16   Thread 0x73aff74006c0 (LWP 8152) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  17   Thread 0x73aff7e006c0 (LWP 8151) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  18   Thread 0x73affd0006c0 (LWP 8150) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  19   Thread 0x73affda006c0 (LWP 8149) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  20   Thread 0x73affe4006c0 (LWP 8148) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  21   Thread 0x73affee006c0 (LWP 8147) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  22   Thread 0x73afff8006c0 (LWP 8146) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38

Thread 22 (Thread 0x73afff8006c0 (LWP 8146) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199743051456, 8417409019976466535, 127199743051456, -1144, 0, 140732836582944, 8417409020358148199, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 21 (Thread 0x73affee006c0 (LWP 8147) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199732565696, 8417412043633442919, 127199732565696, -1144, 0, 140732836582944, 8417412044015124583, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 20 (Thread 0x73affe4006c0 (LWP 8148) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199722079936, 8417410669243908199, 127199722079936, -1144, 0, 140732836582944, 8417410669625589863, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 19 (Thread 0x73affda006c0 (LWP 8149) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199711594176, 8417404896807862375, 127199711594176, -1144, 0, 140732836582944, 8417404897189544039, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 18 (Thread 0x73affd0006c0 (LWP 8150) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199701108416, 8417407920464838759, 127199701108416, -1144, 0, 140732836582944, 8417407920846520423, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 17 (Thread 0x73aff7e006c0 (LWP 8151) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199615125184, 8417427436796231783, 127199615125184, -1144, 0, 140732836582944, 8417427437177913447, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 16 (Thread 0x73aff74006c0 (LWP 8152) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199604639424, 8417426062406697063, 127199604639424, -1144, 0, 140732836582944, 8417426062788378727, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 15 (Thread 0x73aff6a006c0 (LWP 8153) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199594153664, 8417429086063673447, 127199594153664, -1144, 0, 140732836582944, 8417429086445355111, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 14 (Thread 0x73aff60006c0 (LWP 8154) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199583667904, 8417423313627627623, 127199583667904, -1144, 0, 140732836582944, 8417423314009309287, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 13 (Thread 0x73aff56006c0 (LWP 8155) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199573182144, 8417421939238092903, 127199573182144, -1144, 0, 140732836582944, 8417421939619774567, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 12 (Thread 0x73aff4c006c0 (LWP 8156) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001754083 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199562696384, 8417424962895069287, 127199562696384, -1144, 0, 140732836582944, 8417424963276750951, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 11 (Thread 0x73afeb8006c0 (LWP 8157) "pool-spawner"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b00118f52b in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x000073b0011f7043 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199407507136, 8417382631697399911, 127199407507136, -1144, 17, 140732836579600, 8417382632079081575, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#6  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 10 (Thread 0x73afeae006c0 (LWP 8158) "gmain"):
#0  0x000073b000f1b4cd in __GI___poll (fds=0x6289cc0933c0, nfds=2, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
        sc_ret = -516
        sc_cancel_oldtype = 0
        sc_ret = <optimized out>
#1  0x000073b00122466e in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b0011c4a53 in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x000073b0011c4aa9 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199397021376, 8417385655354376295, 127199397021376, -1144, 17, 140732836579392, 8417385655736057959, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#6  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 9 (Thread 0x73afea4006c0 (LWP 8159) "dconf worker"):
#0  0x000073b000f1b4cd in __GI___poll (fds=0x73afa8000b90, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
        sc_ret = -516
        sc_cancel_oldtype = 0
        sc_ret = <optimized out>
#1  0x000073b00122466e in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b0011c4a53 in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x000073afff91c595 in ??? () at /usr/lib/x86_64-linux-gnu/gio/modules/libdconfsettings.so
#4  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199386535616, 8417384280964841575, 127199386535616, -1144, 17, 140732836579808, 8417384281346523239, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#6  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 8 (Thread 0x73afe9a006c0 (LWP 8160) "gdbus"):
#0  0x000073b000f1b4cd in __GI___poll (fds=0x73afa4000b90, nfds=2, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
        sc_ret = -516
        sc_cancel_oldtype = 0
        sc_ret = <optimized out>
#1  0x000073b00122466e in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b0011c5f77 in g_main_loop_run () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x000073b001468a42 in ??? () at /lib/x86_64-linux-gnu/libgio-2.0.so.0
#4  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199376049856, 8417378508528795751, 127199376049856, -1144, 11, 127199386530304, 8417378508910477415, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#6  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 7 (Thread 0x73afd7e006c0 (LWP 8162) "async"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00006289cb472c0c in ??? ()
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199078254272, 8417497805540409447, 127199078254272, -1144, 0, 140732836583088, 8417497805922091111, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 6 (Thread 0x73afd74006c0 (LWP 8163) "gimp-2.10"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b00118f52b in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x000073b00118f58c in g_async_queue_pop () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b00208a0fb in ??? () at /lib/x86_64-linux-gnu/libpangoft2-1.0.so.0
#5  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#6  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199067768512, 8417496431150874727, 127199067768512, -1144, 0, 140732836582080, 8417496431532556391, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#7  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:784

Thread 5 (Thread 0x73afd60006c0 (LWP 8166) "gimp-2.10"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b00118f52b in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x000073b00118f58c in g_async_queue_pop () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b00208a0fb in ??? () at /lib/x86_64-linux-gnu/libpangoft2-1.0.so.0
#5  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#6  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199046796992, 8417493682371805287, 127199046796992, -1144, 11, 140732836582496, 8417493682753486951, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#7  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 4 (Thread 0x73afd6a006c0 (LWP 8195) "swap writer"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b001795a25 in ??? () at /lib/x86_64-linux-gnu/libgegl-0.4.so.0
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199057282752, 8417499454807851111, 127199057282752, -1144, 11, 140732836575248, 8417499455189532775, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 3 (Thread 0x73afe90006c0 (LWP 8203) "paint"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121e40d in g_cond_wait () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00006289cb224869 in ??? ()
#3  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127199365564096, 8417381532185772135, 127199365564096, -1144, 11, 140732836580224, 8417381532567453799, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 2 (Thread 0x73afc8c006c0 (LWP 8204) "pool-gimp-2.10"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
#1  0x000073b00121ed00 in g_cond_wait_until () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x000073b00118f4f3 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x000073b00118f646 in g_async_queue_timeout_pop () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x000073b0011f93df in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x000073b0011f3c82 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#6  0x000073b000e9ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {127198824498880, 8417451351174135911, 127198824498880, -1144, 0, 127199407502528, 8417451351555817575, 8426054327283990631}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#7  0x000073b000f29c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78

Thread 1 (Thread 0x73b000501640 (LWP 8144) "gimp-2.10"):
#0  0x000073b000f1ba9a in __GI___libc_read (nbytes=256, buf=0x7ffeeabb6570, fd=15) at ../sysdeps/unix/sysv/linux/read.c:26
        sc_ret = -512
        sc_cancel_oldtype = 0
        sc_ret = <optimized out>
        sc_ret = <optimized out>
        __arg2 = <optimized out>
        _a3 = <optimized out>
        _a1 = <optimized out>
        resultvar = <optimized out>
        __arg3 = <optimized out>
        __arg1 = <optimized out>
        _a2 = <optimized out>
#1  __GI___libc_read (fd=15, buf=0x7ffeeabb6570, nbytes=256) at ../sysdeps/unix/sysv/linux/read.c:24
#2  0x000073b0020f3144 in gimp_stack_trace_print () at /lib/x86_64-linux-gnu/libgimpbase-2.0.so.0
#3  0x00006289cb19fb41 in ??? ()
#4  0x00006289cb19ff1c in gimp_fatal_error ()
#5  0x00006289cb19ff75 in ??? ()
#6  0x000073b000e45320 in <signal handler called> () at /lib/x86_64-linux-gnu/libc.so.6
#7  0x000073b001c97968 in ??? () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#8  0x000073b001c989ed in gtk_button_set_label () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#9  0x000073b0012d71fa in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#10 0x000073b0012da4b6 in g_object_set_valist () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#11 0x000073b0012da92d in g_object_set () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#12 0x00006289cb1f2445 in ??? ()
#13 0x000073b0012c62fa in g_closure_invoke () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#14 0x000073b0012f590c in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#15 0x000073b0012e6591 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#16 0x000073b0012e67c1 in g_signal_emit_valist () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#17 0x000073b0012e6883 in g_signal_emit () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#18 0x00006289cb4981b3 in gimp_container_remove ()
#19 0x00006289cb518f3c in ??? ()
#20 0x00006289cb497cf4 in gimp_container_clear ()
#21 0x00006289cb498fa5 in ??? ()
#22 0x000073b0012d53fe in g_object_unref () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#23 0x00006289cb1f02de in ??? ()
#24 0x000073b0012d0137 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#25 0x000073b0011a44e3 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#26 0x000073b0012d232b in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#27 0x000073b0012d56c4 in g_object_run_dispose () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#28 0x00006289cb1f1d5f in ??? ()
#29 0x000073b0012c62fa in g_closure_invoke () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#30 0x000073b0012f590c in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#31 0x000073b0012e6591 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#32 0x000073b0012e67c1 in g_signal_emit_valist () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#33 0x000073b0012e6883 in g_signal_emit () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#34 0x000073b0012c62fa in g_closure_invoke () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#35 0x000073b0012f590c in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#36 0x000073b0012e6591 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#37 0x000073b0012e67c1 in g_signal_emit_valist () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#38 0x000073b0012e6883 in g_signal_emit () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#39 0x000073b001c97b99 in ??? () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#40 0x000073b0012c62fa in g_closure_invoke () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#41 0x000073b0012f5a50 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#42 0x000073b0012e6591 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#43 0x000073b0012e67c1 in g_signal_emit_valist () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#44 0x000073b0012e6883 in g_signal_emit () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#45 0x000073b001c983e9 in ??? () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#46 0x000073b001d46420 in ??? () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#47 0x000073b0012c62fa in g_closure_invoke () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#48 0x000073b0012f5f98 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#49 0x000073b0012e5ef2 in ??? () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#50 0x000073b0012e67c1 in g_signal_emit_valist () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#51 0x000073b0012e6883 in g_signal_emit () at /lib/x86_64-linux-gnu/libgobject-2.0.so.0
#52 0x000073b001e85164 in ??? () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#53 0x000073b001d4ce4b in gtk_propagate_event () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#54 0x000073b001d4dd1b in gtk_main_do_event () at /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#55 0x000073b0021c72f6 in ??? () at /lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0
#56 0x000073b0011c55b5 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#57 0x000073b001224717 in ??? () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#58 0x000073b0011c5f77 in g_main_loop_run () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#59 0x00006289cb1a45a0 in app_run ()
#60 0x00006289cb19a35f in main ()
[Inferior 1 (process 8144) detached]
```

---

### Post by #&amp;thj^% on 2024-04-30
Not sure i can help, but was 24.04 an upgrade, or A clean install?

What version Gimp? Snap or .Deb
```
 apt policy gimp
gimp:
  Installed: 2.10.36-3build3
  Candidate: 2.10.36-3build3
  Version table:
 *** 2.10.36-3build3 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by hrsetrdr on 2024-04-30
> **1fallen said:**
> Not sure i can help, but was 24.04 an upgrade, or A clean install?

What version Gimp? Snap or .Deb
```
 apt policy gimp
gimp:
  Installed: 2.10.36-3build3
  Candidate: 2.10.36-3build3
  Version table:
 *** 2.10.36-3build3 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

24.04 was a clean install.   I just installed Gimp using APT, how could you tell if the Gimp pkg was a snap or .deb?

---

### Post by #&amp;thj^% on 2024-04-30
> **hrsetrdr said:**
> 24.04 was a clean install.   I just installed Gimp using APT, how could you tell if the Gimp pkg was a snap or .deb?
By this:
```
apt policy gimp
```
It dose not look like it's been snaped ATM that's good.
Have you logged out and back in again?
Also Wayland might be in play here, have you tried a X11 session?

If it keeps " seg-faulting" it's also available on Flatpak:
```
[code]flatpak search gimp
Name                              Description                                                                                                                               Application ID                       Version   Branch   Remotes
GIMP User Manual                  GIMP User Manual                                                                                                                          org.gimp.GIMP.Manual                 2.10      2.10     flathub
GNU Image Manipulation Program    Create images and edit photographs                                                                                                        org.gimp.GIMP                        2.10.36   stable   flathub

```

Or you might get lucky with:
```
sudo apt install --reinstall gimp
```

Nothing in your de-bug is jumping out as to why it fails.

---

### Post by hrsetrdr on 2024-04-30
I reinstalled Gimp, but Gimp still crashes.   I'll do a snap or Flatpack install.

---

### Post by #&amp;thj^% on 2024-04-30
> **hrsetrdr said:**
>  I'll do a snap or Flatpack install.

I don't think it has a snap install yet. I could be wrong though.

---

### Post by hrsetrdr on 2024-04-30
Got Gimp from [https://snapcraft.io/store](https://snapcraft.io/store).  Gimp still crashes.  When I get a chance I'll look for bug reports.

---

### Post by #&amp;thj^% on 2024-04-30
Let us know, also you might have a peek in: "/home/<your user name>/.config/GIMP/2.10/CrashLog/"

FWIW Gimp from flatpak also runs nicely on my end.

---

### Post by hrsetrdr on 2024-05-03
> **hrsetrdr said:**
> Got Gimp from [https://snapcraft.io/store](https://snapcraft.io/store).  Gimp still crashes.  When I get a chance I'll look for bug reports.

I believe I was mistaken, I discovered a 2nd version of Gimp upon right-clicking an image, the working version presumably from the Snap store.   The weird things is, they both claim to be Gimp 2.10.36.  ?

---

### Post by deadflowr on 2024-05-03
> **hrsetrdr said:**
> I believe I was mistaken, I discovered a 2nd version of Gimp upon right-clicking an image, the working version presumably from the Snap store.   The weird things is, they both claim to be Gimp 2.10.36.  ?

Easy way to tell if it's the snap version is to try accessing help.
The snap version can't access the online manual.

---

### Post by marco-emme on 2024-05-04
I have a similar problem. I use Gimp and it works fine but when I close it I get an error warning
Ubuntu 24.04 fresh install
```
<!-- Copy-paste this whole debug data to report to developers -->


```
GNU Image Manipulation Program version 2.10.36
git-describe: GIMP_2_10_36
Build: unknown rev 0 for linux
# C compiler #
    Using built-in specs.
    COLLECT_GCC=gcc
    COLLECT_LTO_WRAPPER=/usr/libexec/gcc/x86_64-linux-gnu/13/lto-wrapper
    OFFLOAD_TARGET_NAMES=nvptx-none:amdgcn-amdhsa
    OFFLOAD_TARGET_DEFAULT=1
    Target: x86_64-linux-gnu
    Configured with: ../src/configure -v --with-pkgversion='Ubuntu 13.2.0-23ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-13/README.Bugs --enable-languages=c,ada,c++,go,d,fortran,objc,obj-c++,m2 --prefix=/usr --with-gcc-major-version-only --program-suffix=-13 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/libexec --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-libstdcxx-backtrace --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --enable-default-pie --with-system-zlib --enable-libphobos-checking=release --with-target-system-zlib=auto --enable-objc-gc=auto --enable-multiarch --disable-werror --enable-cet --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none=/build/gcc-13-OiuXZC/gcc-13-13.2.0/debian/tmp-nvptx/usr,amdgcn-amdhsa=/build/gcc-13-OiuXZC/gcc-13-13.2.0/debian/tmp-gcn/usr --enable-offload-defaulted --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
    Thread model: posix
    Supported LTO compression algorithms: zlib zstd
    gcc version 13.2.0 (Ubuntu 13.2.0-23ubuntu3) 

# Libraries #
using babl version 0.1.108 (compiled against version 0.1.108)
using GEGL version 0.4.48 (compiled against version 0.4.48)
using GLib version 2.80.0 (compiled against version 2.80.0)
using GdkPixbuf version 2.42.10 (compiled against version 2.42.10)
using GTK+ version 2.24.33 (compiled against version 2.24.33)
using Pango version 1.52.1 (compiled against version 1.52.1)
using Fontconfig version 2.15.0 (compiled against version 2.15.0)
using Cairo version 1.18.0 (compiled against version 1.18.0)

```
> fatal error: Errore di segmentazione

Stack trace:
```

# Stack traces obtained from PID 103572 - Thread 103572 #


This GDB supports auto-downloading debuginfo from the following URLs:
  <https://debuginfod.ubuntu.com>
Enable debuginfod for this session? (y or [n]) [answered N; input not from terminal]
Debuginfod has been disabled.
To make this setting permanent, add 'set debuginfod enabled off' to .gdbinit.
[New LWP 103862]
[New LWP 103852]
[New LWP 103849]
[New LWP 103613]
[New LWP 103610]
[New LWP 103608]
[New LWP 103604]
[New LWP 103603]
[New LWP 103602]
[New LWP 103601]
[New LWP 103600]
[New LWP 103599]
[New LWP 103598]
[New LWP 103597]
[New LWP 103596]
[New LWP 103595]
[New LWP 103594]
[New LWP 103593]
[New LWP 103592]
[New LWP 103591]
[New LWP 103590]
[New LWP 103589]
[New LWP 103588]
[New LWP 103587]
[New LWP 103586]
[New LWP 103585]
[New LWP 103584]
[New LWP 103583]
[New LWP 103582]
[New LWP 103581]
[New LWP 103580]
[New LWP 103579]
[New LWP 103578]
[New LWP 103577]
[New LWP 103576]
[New LWP 103575]
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
0x00007a708311ba9a in __GI___libc_read (nbytes=256, buf=0x7fff32d7ee70, fd=18) at ../sysdeps/unix/sysv/linux/read.c:26
  Id   Target Id                                           Frame 
* 1    Thread 0x7a7082af2640 (LWP 103572) "gimp-2.10"      0x00007a708311ba9a in __GI___libc_read (nbytes=256, buf=0x7fff32d7ee70, fd=18) at ../sysdeps/unix/sysv/linux/read.c:26
  2    Thread 0x7a7017e006c0 (LWP 103862) "pool-gimp-2.10" syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  3    Thread 0x7a7039a006c0 (LWP 103852) "paint"          syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  4    Thread 0x7a703ae006c0 (LWP 103849) "swap writer"    syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  5    Thread 0x7a703a4006c0 (LWP 103613) "gimp-2.10"      syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  6    Thread 0x7a703b8006c0 (LWP 103610) "gimp-2.10"      syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  7    Thread 0x7a70454006c0 (LWP 103608) "async"          syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  8    Thread 0x7a704e0006c0 (LWP 103604) "gdbus"          0x00007a708311b4cd in __GI___poll (fds=0x7a6fc8000b90, nfds=3, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
  9    Thread 0x7a704ea006c0 (LWP 103603) "gmain"          0x00007a708311b4cd in __GI___poll (fds=0x5ffc8eb8a840, nfds=2, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
  10   Thread 0x7a704f4006c0 (LWP 103602) "pool-spawner"   syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  11   Thread 0x7a7058c006c0 (LWP 103601) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  12   Thread 0x7a70596006c0 (LWP 103600) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  13   Thread 0x7a705a0006c0 (LWP 103599) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  14   Thread 0x7a705aa006c0 (LWP 103598) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  15   Thread 0x7a705b4006c0 (LWP 103597) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  16   Thread 0x7a705be006c0 (LWP 103596) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  17   Thread 0x7a7060c006c0 (LWP 103595) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  18   Thread 0x7a70616006c0 (LWP 103594) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  19   Thread 0x7a70620006c0 (LWP 103593) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  20   Thread 0x7a7062a006c0 (LWP 103592) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  21   Thread 0x7a70634006c0 (LWP 103591) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  22   Thread 0x7a7063e006c0 (LWP 103590) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  23   Thread 0x7a7074c006c0 (LWP 103589) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  24   Thread 0x7a70756006c0 (LWP 103588) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  25   Thread 0x7a70760006c0 (LWP 103587) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  26   Thread 0x7a7076a006c0 (LWP 103586) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  27   Thread 0x7a70774006c0 (LWP 103585) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  28   Thread 0x7a7077e006c0 (LWP 103584) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  29   Thread 0x7a707cc006c0 (LWP 103583) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  30   Thread 0x7a707d6006c0 (LWP 103582) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  31   Thread 0x7a707e0006c0 (LWP 103581) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  32   Thread 0x7a707ea006c0 (LWP 103580) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  33   Thread 0x7a707f4006c0 (LWP 103579) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  34   Thread 0x7a707fe006c0 (LWP 103578) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  35   Thread 0x7a70808006c0 (LWP 103577) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  36   Thread 0x7a70812006c0 (LWP 103576) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
  37   Thread 0x7a7081c006c0 (LWP 103575) "worker"         syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38

Thread 37 (Thread 0x7a7081c006c0 (LWP 103575) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623631771328, -5840473759805717753, 134623631771328, -1144, 0, 140734046412608, -5840473759356927225, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 36 (Thread 0x7a70812006c0 (LWP 103576) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623621285568, -5840472385416183033, 134623621285568, -1144, 0, 140734046412608, -5840472384967392505, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 35 (Thread 0x7a70808006c0 (LWP 103577) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623610799808, -5840469911515020537, 134623610799808, -1144, 0, 140734046412608, -5840469911066230009, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 34 (Thread 0x7a707fe006c0 (LWP 103578) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623600314048, -5840178266055752953, 134623600314048, -1144, 0, 140734046412608, -5840178265606962425, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 33 (Thread 0x7a707f4006c0 (LWP 103579) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623589828288, -5840177991177846009, 134623589828288, -1144, 0, 140734046412608, -5840177990729055481, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 32 (Thread 0x7a707ea006c0 (LWP 103580) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623579342528, -5840176616788311289, 134623579342528, -1144, 0, 140734046412608, -5840176616339520761, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 31 (Thread 0x7a707e0006c0 (LWP 103581) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623568856768, -5840182938980171001, 134623568856768, -1144, 0, 140734046412608, -5840182938531380473, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 30 (Thread 0x7a707d6006c0 (LWP 103582) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623558371008, -5840181564590636281, 134623558371008, -1144, 0, 140734046412608, -5840181564141845753, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 29 (Thread 0x7a707cc006c0 (LWP 103583) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623547885248, -5840181289712729337, 134623547885248, -1144, 0, 140734046412608, -5840181289263938809, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 28 (Thread 0x7a7077e006c0 (LWP 103584) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623466096320, -5840160673869708537, 134623466096320, -1144, 0, 140734046412608, -5840160673420918009, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 27 (Thread 0x7a70774006c0 (LWP 103585) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623455610560, -5840160398991801593, 134623455610560, -1144, 0, 140734046412608, -5840160398543011065, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 26 (Thread 0x7a7076a006c0 (LWP 103586) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623445124800, -5840159024602266873, 134623445124800, -1144, 0, 140734046412608, -5840159024153476345, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 25 (Thread 0x7a70760006c0 (LWP 103587) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623434639040, -5840165346794126585, 134623434639040, -1144, 0, 140734046412608, -5840165346345336057, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 24 (Thread 0x7a70756006c0 (LWP 103588) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623424153280, -5840163972404591865, 134623424153280, -1144, 0, 140734046412608, -5840163971955801337, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 23 (Thread 0x7a7074c006c0 (LWP 103589) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623413667520, -5840163697526684921, 134623413667520, -1144, 0, 140734046412608, -5840163697077894393, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 22 (Thread 0x7a7063e006c0 (LWP 103590) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623130552000, -5840116693404597497, 134623130552000, -1144, 0, 140734046412608, -5840116692955806969, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 21 (Thread 0x7a70634006c0 (LWP 103591) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623120066240, -5840116418526690553, 134623120066240, -1144, 0, 140734046412608, -5840116418077900025, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 20 (Thread 0x7a7062a006c0 (LWP 103592) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623109580480, -5840115044137155833, 134623109580480, -1144, 0, 140734046412608, -5840115043688365305, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 19 (Thread 0x7a70620006c0 (LWP 103593) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623099094720, -5840121366329015545, 134623099094720, -1144, 0, 140734046412608, -5840121365880225017, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 18 (Thread 0x7a70616006c0 (LWP 103594) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623088608960, -5840119991939480825, 134623088608960, -1144, 0, 140734046412608, -5840119991490690297, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 17 (Thread 0x7a7060c006c0 (LWP 103595) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134623078123200, -5840119717061573881, 134623078123200, -1144, 0, 140734046412608, -5840119716612783353, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 16 (Thread 0x7a705be006c0 (LWP 103596) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622996334272, -5840099101218553081, 134622996334272, -1144, 0, 140734046412608, -5840099100769762553, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 15 (Thread 0x7a705b4006c0 (LWP 103597) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622985848512, -5840098826340646137, 134622985848512, -1144, 0, 140734046412608, -5840098825891855609, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 14 (Thread 0x7a705aa006c0 (LWP 103598) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622975362752, -5840097451951111417, 134622975362752, -1144, 0, 140734046412608, -5840097451502320889, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 13 (Thread 0x7a705a0006c0 (LWP 103599) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622964876992, -5840103774142971129, 134622964876992, -1144, 0, 140734046412608, -5840103773694180601, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 12 (Thread 0x7a70596006c0 (LWP 103600) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622954391232, -5840102399753436409, 134622954391232, -1144, 0, 140734046412608, -5840102399304645881, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 11 (Thread 0x7a7058c006c0 (LWP 103601) "worker"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839a3083 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622943905472, -5840102124875529465, 134622943905472, -1144, 0, 140734046412608, -5840102124426738937, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 10 (Thread 0x7a704f4006c0 (LWP 103602) "pool-spawner"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70833d352b in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#3  0x00007a708343b043 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#5  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622784521920, -5840072438061579513, 134622784521920, -1144, 11, 140734046412624, -5840072437612788985, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#6  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 9 (Thread 0x7a704ea006c0 (LWP 103603) "gmain"):
#0  0x00007a708311b4cd in __GI___poll (fds=0x5ffc8eb8a840, nfds=2, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
        sc_ret = -516
        sc_cancel_oldtype = 0
        sc_ret = <optimized out>
#1  0x00007a708346866e in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a7083408a53 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#3  0x00007a7083408aa9 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#5  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622774036160, -5840071063672044793, 134622774036160, -1144, 11, 140734046412416, -5840071063223254265, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#6  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 8 (Thread 0x7a704e0006c0 (LWP 103604) "gdbus"):
#0  0x00007a708311b4cd in __GI___poll (fds=0x7a6fc8000b90, nfds=3, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
        sc_ret = -516
        sc_cancel_oldtype = 0
        sc_ret = <optimized out>
#1  0x00007a708346866e in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a7083409f77 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#3  0x00007a70836aca42 in ?? () from /lib/x86_64-linux-gnu/libgio-2.0.so.0
No symbol table info available.
#4  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#5  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622763550400, -5840077385863904505, 134622763550400, -1144, 11, 140734046412768, -5840077385415113977, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#6  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 7 (Thread 0x7a70454006c0 (LWP 103608) "async"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00005ffc8cab2c0c in ?? ()
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622616749760, -5840059243922046201, 134622616749760, -1144, 0, 140734046412752, -5840059243473255673, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 6 (Thread 0x7a703b8006c0 (LWP 103610) "gimp-2.10"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70833d352b in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#3  0x00007a70833d358c in g_async_queue_pop () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a70842cc0fb in ?? () from /lib/x86_64-linux-gnu/libpangoft2-1.0.so.0
No symbol table info available.
#5  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#6  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622453171904, -5840309382817365241, 134622453171904, -1144, 0, 140734046411744, -5840309382368574713, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#7  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 5 (Thread 0x7a703a4006c0 (LWP 103613) "gimp-2.10"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70833d352b in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#3  0x00007a70833d358c in g_async_queue_pop () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a70842cc0fb in ?? () from /lib/x86_64-linux-gnu/libpangoft2-1.0.so.0
No symbol table info available.
#5  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#6  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622432200384, -5840307733549923577, 134622432200384, -1144, 11, 140734046412160, -5840307733101133049, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#7  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 4 (Thread 0x7a703ae006c0 (LWP 103849) "swap writer"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70839e4a25 in ?? () from /lib/x86_64-linux-gnu/libgegl-0.4.so.0
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622442686144, -5840308008427830521, 134622442686144, -1144, 11, 140734046398720, -5840308007979039993, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 3 (Thread 0x7a7039a006c0 (LWP 103852) "paint"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a708346240d in g_cond_wait () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00005ffc8c864869 in ?? ()
No symbol table info available.
#3  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134622421714624, -5840315155253411065, 134622421714624, -1144, 11, 140734046409888, -5840315154804620537, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#5  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 2 (Thread 0x7a7017e006c0 (LWP 103862) "pool-gimp-2.10"):
#0  syscall () at ../sysdeps/unix/sysv/linux/x86_64/syscall.S:38
No locals.
#1  0x00007a7083462d00 in g_cond_wait_until () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#2  0x00007a70833d34f3 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#3  0x00007a70833d3646 in g_async_queue_timeout_pop () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#4  0x00007a708343d3df in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#5  0x00007a7083437c82 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#6  0x00007a708309ca94 in start_thread (arg=<optimized out>) at ./nptl/pthread_create.c:447
        ret = <optimized out>
        pd = <optimized out>
        out = <optimized out>
        unwind_buf = {cancel_jmp_buf = {{jmp_buf = {134621855483584, -5840231042613886201, 134621855483584, -1144, 0, 134622784517312, -5840231042165095673, -5840467901551721721}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x0, 0x0}, data = {prev = 0x0, cleanup = 0x0, canceltype = 0}}}
        not_first_call = <optimized out>
#7  0x00007a7083129c3c in clone3 () at ../sysdeps/unix/sysv/linux/x86_64/clone3.S:78
No locals.

Thread 1 (Thread 0x7a7082af2640 (LWP 103572) "gimp-2.10"):
#0  0x00007a708311ba9a in __GI___libc_read (nbytes=256, buf=0x7fff32d7ee70, fd=18) at ../sysdeps/unix/sysv/linux/read.c:26
        sc_ret = -512
        sc_cancel_oldtype = 0
        sc_ret = <optimized out>
        sc_ret = <optimized out>
        __arg2 = <optimized out>
        _a3 = <optimized out>
        _a1 = <optimized out>
        resultvar = <optimized out>
        __arg3 = <optimized out>
        __arg1 = <optimized out>
        _a2 = <optimized out>
#1  __GI___libc_read (fd=18, buf=0x7fff32d7ee70, nbytes=256) at ../sysdeps/unix/sysv/linux/read.c:24
No locals.
#2  0x00007a7084335144 in gimp_stack_trace_print () from /lib/x86_64-linux-gnu/libgimpbase-2.0.so.0
No symbol table info available.
#3  0x00005ffc8c7dfb41 in ?? ()
No symbol table info available.
#4  0x00005ffc8c7dff1c in gimp_fatal_error ()
No symbol table info available.
#5  0x00005ffc8c7dff75 in ?? ()
No symbol table info available.
#6  <signal handler called>
No locals.
#7  0x00007a7083e97968 in ?? () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0x00007a7083e989ed in gtk_button_set_label () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0x00007a708351b1fa in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#10 0x00007a708351e4b6 in g_object_set_valist () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#11 0x00007a708351e92d in g_object_set () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#12 0x00005ffc8c832445 in ?? ()
No symbol table info available.
#13 0x00007a708350a2fa in g_closure_invoke () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#14 0x00007a708353990c in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#15 0x00007a708352a591 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#16 0x00007a708352a7c1 in g_signal_emit_valist () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#17 0x00007a708352a883 in g_signal_emit () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#18 0x00005ffc8cad81b3 in gimp_container_remove ()
No symbol table info available.
#19 0x00005ffc8cb58f3c in ?? ()
No symbol table info available.
#20 0x00005ffc8cad7cf4 in gimp_container_clear ()
No symbol table info available.
#21 0x00005ffc8cad8fa5 in ?? ()
No symbol table info available.
#22 0x00007a70835193fe in g_object_unref () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#23 0x00005ffc8c8302de in ?? ()
No symbol table info available.
#24 0x00007a7083514137 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#25 0x00007a70833e84e3 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#26 0x00007a708351632b in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#27 0x00007a70835196c4 in g_object_run_dispose () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#28 0x00005ffc8c831d5f in ?? ()
No symbol table info available.
#29 0x00007a708350a2fa in g_closure_invoke () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#30 0x00007a708353990c in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#31 0x00007a708352a591 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#32 0x00007a708352a7c1 in g_signal_emit_valist () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#33 0x00007a708352a883 in g_signal_emit () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#34 0x00007a708350a2fa in g_closure_invoke () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#35 0x00007a708353990c in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#36 0x00007a708352a591 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#37 0x00007a708352a7c1 in g_signal_emit_valist () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#38 0x00007a708352a883 in g_signal_emit () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#39 0x00007a7083e97b99 in ?? () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#40 0x00007a708350a2fa in g_closure_invoke () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#41 0x00007a7083539a50 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#42 0x00007a708352a591 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#43 0x00007a708352a7c1 in g_signal_emit_valist () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#44 0x00007a708352a883 in g_signal_emit () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#45 0x00007a7083e983e9 in ?? () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#46 0x00007a7083f46420 in ?? () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#47 0x00007a708350a2fa in g_closure_invoke () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#48 0x00007a7083539f98 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#49 0x00007a7083529ef2 in ?? () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#50 0x00007a708352a7c1 in g_signal_emit_valist () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#51 0x00007a708352a883 in g_signal_emit () from /lib/x86_64-linux-gnu/libgobject-2.0.so.0
No symbol table info available.
#52 0x00007a7084085164 in ?? () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#53 0x00007a7083f4ce4b in gtk_propagate_event () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#54 0x00007a7083f4dd1b in gtk_main_do_event () from /lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
No symbol table info available.
#55 0x00007a70844092f6 in ?? () from /lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0
No symbol table info available.
#56 0x00007a70834095b5 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#57 0x00007a7083468717 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#58 0x00007a7083409f77 in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
No symbol table info available.
#59 0x00005ffc8c7e45a0 in app_run ()
No symbol table info available.
#60 0x00005ffc8c7da35f in main ()
No symbol table info available.
[Inferior 1 (process 103572) detached]

```
```

---

### Post by hrsetrdr on 2024-05-04
Using the Gimp package from [https://snapcraft.io/store](https://snapcraft.io/store) worked for me, then I uninstalled the crashing version.

---

### Post by marco-emme on 2024-05-05
You're right, it works

---

