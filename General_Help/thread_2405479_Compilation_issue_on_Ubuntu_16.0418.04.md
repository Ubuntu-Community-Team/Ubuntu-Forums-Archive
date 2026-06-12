---
title: "Compilation issue on Ubuntu 16.04/18.04"
date: 2018-11-06
forum: General Help
---

### Post by MZ250Supa5 on 2018-11-06
I posted about this before, but I'm guessing the title threw people, (and obviously me, as I mistitled it) and it's a compilation issue, not a monitor issue. For the best part of two years I've been using my Parblo Coast 22 on Ubuntu successfully after finding a set of drivers online. These need compiling  of course, and re-installing every time a kernel changes. Up until now this hasn't been much of an issue, though sometimes it's taken a few days for the updates have been added so that I can re-compile and install the drivers. All I've done in tat situation is to boot to a previous kernel version for a few days, and then re-compile and install. 

However, this approach no longer works, and I am left with a pen monitor that I can no longer use on Linux,(still works fine on Windows...). When I try to compile I get this output from the terminal session:

```
padi@branwen:~$ cd Monoprice_22_linux_kernel_module-master/
padi@branwen:~/Monoprice_22_linux_kernel_module-master$ make
gcc detach_usbhid.c -I/usr/include/libusb-1.0  -L/lib/-linux-gnu/libusb-1.0.so.0 -lusb-1.0 -o detach_usbhid
make -C /lib/modules/4.15.0-38-generic/build M=/home/padi/Monoprice_22_linux_kernel_module-master modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-38-generic'
  CC [M]  /home/padi/Monoprice_22_linux_kernel_module-master/mono_22.o
In file included from ./include/linux/jiffies.h:7:0,
                 from /home/padi/Monoprice_22_linux_kernel_module-master/mono_22.c:34:
./include/linux/kernel.h:6:20: fatal error: stdarg.h: No such file or directory
compilation terminated.
scripts/Makefile.build:339: recipe for target '/home/padi/Monoprice_22_linux_kernel_module-master/mono_22.o' failed
make[2]: *** [/home/padi/Monoprice_22_linux_kernel_module-master/mono_22.o] Error 1
Makefile:1551: recipe for target '_module_/home/padi/Monoprice_22_linux_kernel_module-master' failed
make[1]: *** [_module_/home/padi/Monoprice_22_linux_kernel_module-master] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-38-generic'
Makefile:10: recipe for target 'all' failed
make: *** [all] Error 2
padi@branwen:~/Monoprice_22_linux_kernel_module-master$ 

```

I've tried contacting the project maintainer, but haven't received a response. I'd love to be able to solve this issue myself, and I believe, from the searching I've done, that the issue lies here:

```
./include/linux/kernel.h:6:20: fatal error: stdarg.h: No such file or directory
compilation terminated.
```

How would I go about solving that issue? Anyone got any ideas?

---

### Post by jeremy31 on 2018-11-07
Is the build-essential package installed?  What does ```
locate stdarg.h
```
Result with?

---

### Post by dragonfly41 on 2018-11-07
A suggestion .. before running the suggested command .. locate stdarg.h
run this command first .. sudo updatedb
and sit back for quite some time until all files are indexed.

I find that I need to run updatedb if there have been recent changes to filesystem
resulting in *new files* not being located.

---

### Post by MZ250Supa5 on 2018-11-17
This is the output I get when running the suggested command, after I've updated as per dragonfly41's advice:

```
padi@branwen:~$ locate stdarg.h
/home/padi/src/blender-deps/LLVM-3.4/tools/clang/lib/Headers/stdarg.h
/opt/lib/llvm-3.4/lib/clang/3.4/include/stdarg.h
/usr/include/c++/5/tr1/stdarg.h
/usr/lib/gcc/x86_64-linux-gnu/5/include/cross-stdarg.h
/usr/lib/gcc/x86_64-linux-gnu/5/include/stdarg.h
padi@branwen:~$ 

```

---

