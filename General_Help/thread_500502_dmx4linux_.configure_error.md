---
title: "dmx4linux ./configure error"
date: 2007-07-14
forum: General Help
---

### Post by nkwai on 2007-07-14
Hi, 
i'm trying to install dmx4linux 2.5, but when I do "./configure", I get this error "./configure: 6: Syntax error: "(" unexpected" the sixth line of the file is the following "function abort ()" and is the first line of code (the other 5 are comments).
can someone help me? have no idea whats wrong.
Thank you.

---

### Post by Mr. C. on 2007-07-14
Try :

bash ./configure

MrC

---

### Post by geraldm on 2007-07-14
I have no idea what is wrong.  The script runs fine here.
I am using:
% /bin/sh --version
GNU bash, version 3.00.16(1)-release (i386-pc-linux-gnu)
Copyright (C) 2004 Free Software Foundation, Inc.

check for a more current version of bash than the one you are using.
Also, for problems with so few code lines, it is helpful to just post the 
lines.

Gerald

---

### Post by nkwai on 2007-07-14
> **Mr. C. said:**
> Try :

bash ./configure

MrC

Thank you vey much it worked.

Can someone just explain me the difference between "./configure" and "bash ./configure"

Thank you.

---

### Post by nkwai on 2007-07-14
Can someone help me with the make too?

this is the output:
```
nkwai@nkwai-laptop:~/dmx4linux-2.5$ make
make -C libs all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.5/libs'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.5/libs'
make -C tools all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.5/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.5/tools'
make -C drivers all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.5/drivers'
make -C dmxdev all
make[2]: Entering directory `/home/nkwai/dmx4linux-2.5/drivers/dmxdev'
gcc -O2 -Wall -I/home/nkwai/dmx4linux-2.5/include -I/usr/src/linux/include -Wstrict-prototypes -D__KERNEL__ -DMODULE -DDMXVERSION=\"2.5\" -DMODVERSIONS -include /usr/src/linux/include/linux/modversions.h -DDMXOUTMINOR=223 -DDMXINMINOR=224 -DVERSIONMAJOR=2 -DVERSIONMINOR=5   -c -o dmx_dev.o dmx_dev.c
cc1: error: /usr/src/linux/include/linux/modversions.h: No such file or directory
In file included from /usr/src/linux/include/linux/rwsem.h:26,
                 from /usr/src/linux/include/asm/semaphore.h:42,
                 from /usr/src/linux/include/linux/sched.h:57,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/fileinfo.h:26,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:54,
                 from dmx_dev.c:28:
/usr/src/linux/include/asm/rwsem.h: In function ‘__down_read’:
/usr/src/linux/include/asm/rwsem.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux/include/asm/rwsem.h: In function ‘__down_write’:
/usr/src/linux/include/asm/rwsem.h:157: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux/include/asm/rwsem.h: In function ‘__up_read’:
/usr/src/linux/include/asm/rwsem.h:194: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux/include/asm/rwsem.h:188: warning: unused variable ‘tmp’
/usr/src/linux/include/asm/rwsem.h: In function ‘__up_write’:
/usr/src/linux/include/asm/rwsem.h:220: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux/include/asm/rwsem.h: In function ‘__downgrade_write’:
/usr/src/linux/include/asm/rwsem.h:245: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /usr/src/linux/include/linux/sched.h:57,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/fileinfo.h:26,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:54,
                 from dmx_dev.c:28:
/usr/src/linux/include/asm/semaphore.h: In function ‘down’:
/usr/src/linux/include/asm/semaphore.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux/include/asm/semaphore.h: In function ‘down_interruptible’:
/usr/src/linux/include/asm/semaphore.h:130: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux/include/asm/semaphore.h: In function ‘down_trylock’:
/usr/src/linux/include/asm/semaphore.h:155: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux/include/asm/semaphore.h: In function ‘up’:
/usr/src/linux/include/asm/semaphore.h:179: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
dmx_dev.c: In function ‘dmxout_to_user’:
dmx_dev.c:85: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
dmx_dev.c: In function ‘dmxin_to_user’:
dmx_dev.c:156: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
dmx_dev.c: In function ‘DMXDev_read’:
dmx_dev.c:202: warning: implicit declaration of function ‘verify_area’
dmx_dev.c:260: warning: pointer targets in passing argument 2 of ‘info->to_user’ differ in signedness
dmx_dev.c: In function ‘dmx_universe_signal_changed’:
dmx_dev.c:319: error: invalid lvalue in unary ‘&’
dmx_dev.c: In function ‘DMXDev_write’:
dmx_dev.c:348: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
dmx_dev.c: In function ‘DMXDev_ioctl’:
dmx_dev.c:526: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
dmx_dev.c:542: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
dmx_dev.c:579: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
dmx_dev.c:601: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
dmx_dev.c:622: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
dmx_dev.c:668: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
dmx_dev.c:684: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
dmx_dev.c:702: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
dmx_dev.c:723: warning: ignoring return value of ‘copy_to_user’, declared with attribute warn_unused_result
dmx_dev.c:739: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
dmx_dev.c:790: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
make[2]: *** [dmx_dev.o] Error 1
make[2]: Leaving directory `/home/nkwai/dmx4linux-2.5/drivers/dmxdev'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.5/drivers'
make: *** [all] Error 2

```

---

### Post by Mr. C. on 2007-07-14
> **nkwai said:**
> Thank you vey much it worked.

Can someone just explain me the difference between "./configure" and "bash ./configure"

Thank you.

The **./configure** usage tells the shell to run the command **configure** which is located in the current directory.  The shell tells the system to **exec** this program.  However, because the program is really a shell script, and it has as its first line **#!/bin/sh**, the kernel actually invokes **/bin/sh**, and passes as its first argument **./configure**.  The actual exec call becomes:
```

/bin/sh ./configure
```

The **bash ./configure** command and argument do essentially the same thing.  Your current shell exec's the command **bash**, with the argument **./configure**.  The command and arguments given to exec are:
```

/bin/bash ./configure
```

Note that the only difference now, is **bash** vs. **sh**.

The problem you saw occurred because your **/bin/sh** does not support the syntax used in the **configure** script.  This occurred either because you changed your shell (eg. to dash), or because your **/bin/sh** is not **bash**, but is really the older Bourne shell **sh** which does not support functions.

MrC

---

### Post by Mr. C. on 2007-07-14
> **nkwai said:**
> Can someone help me with the make too?

...
```
cc1: error: /usr/src/linux/include/linux/modversions.h: No such file or directory
```
...


You are missing the kernel include files, necessary to build kernel modules.  I don't recall the exact name of the headers package; run Synaptec and search for kernel, and within those results, find the kernel headers and install them.

MrC

---

### Post by nkwai on 2007-07-14
Changed the kernel source, now the error is as follows:
```
nkwai@nkwai-laptop:~/dmx4linux-2.5$ make
make -C libs all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.5/libs'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.5/libs'
make -C tools all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.5/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.5/tools'
make -C drivers all
make[1]: Entering directory `/home/nkwai/dmx4linux-2.5/drivers'
make -C dmxdev all
make[2]: Entering directory `/home/nkwai/dmx4linux-2.5/drivers/dmxdev'
gcc -O2 -Wall -I/home/nkwai/dmx4linux-2.5/include -I/lib/modules/2.6.20-16-386/build/include -Wstrict-prototypes -D__KERNEL__ -DMODULE -DDMXVERSION=\"2.5\" -DMODVERSIONS -include /lib/modules/2.6.20-16-386/build/include/linux/modversions.h -DDMXOUTMINOR=223 -DDMXINMINOR=224 -DVERSIONMAJOR=2 -DVERSIONMINOR=5   -c -o dmx_dev.o dmx_dev.c
cc1: error: /lib/modules/2.6.20-16-386/build/include/linux/modversions.h: No such file or directory
In file included from dmx_dev.c:28:
/home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:24:26: error: linux/config.h: No such file or directory
/home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:28:2: error: #error Linux Kernel needs Modules support for DMX4Linux
In file included from /lib/modules/2.6.20-16-386/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.20-16-386/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.20-16-386/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.20-16-386/build/include/linux/spinlock.h:49,
                 from /home/nkwai/dmx4linux-2.5/include/dmx/dmxconfig.h:67,
                 from /home/nkwai/dmx4linux-2.5/include/dmx/dmxdev.h:24,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:52,
                 from dmx_dev.c:28:
/lib/modules/2.6.20-16-386/build/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.20-16-386/build/include/asm/processor.h:82: error: requested alignment is not a constant
/lib/modules/2.6.20-16-386/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.20-16-386/build/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-386/build/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-386/build/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.20-16-386/build/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.20-16-386/build/include/linux/sched.h:51,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/fileinfo.h:26,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:54,
                 from dmx_dev.c:28:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /lib/modules/2.6.20-16-386/build/include/linux/sched.h:51,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/fileinfo.h:26,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:54,
                 from dmx_dev.c:28:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:274: error: for each function it appears in.)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/lib/modules/2.6.20-16-386/build/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /lib/modules/2.6.20-16-386/build/include/linux/aio.h:5,
                 from /lib/modules/2.6.20-16-386/build/include/linux/sched.h:260,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/fileinfo.h:26,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:54,
                 from dmx_dev.c:28:
/lib/modules/2.6.20-16-386/build/include/linux/workqueue.h: In function ‘cancel_delayed_work’:
/lib/modules/2.6.20-16-386/build/include/linux/workqueue.h:203: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /home/nkwai/dmx4linux-2.5/include/dmxdev/fileinfo.h:26,
                 from /home/nkwai/dmx4linux-2.5/include/dmxdev/dmxdevP.h:54,
                 from dmx_dev.c:28:
/lib/modules/2.6.20-16-386/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/lib/modules/2.6.20-16-386/build/include/linux/sched.h:1309: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.20-16-386/build/include/linux/sched.h:1311: warning: implicit declaration of function ‘local_irq_restore’
In file included from /lib/modules/2.6.20-16-386/build/include/linux/module.h:21,
                 from dmx_dev.c:32:
/lib/modules/2.6.20-16-386/build/include/asm/module.h:62:2: error: #error unknown processor family
dmx_dev.c:33:35: error: linux/devfs_fs_kernel.h: No such file or directory
dmx_dev.c: In function ‘DMXDev_read’:
dmx_dev.c:202: warning: implicit declaration of function ‘verify_area’
dmx_dev.c:260: warning: pointer targets in passing argument 2 of ‘info->to_user’ differ in signedness
dmx_dev.c: In function ‘dmx_universe_signal_changed’:
dmx_dev.c:319: error: invalid lvalue in unary ‘&’
dmx_dev.c: In function ‘dmx_dev_init’:
dmx_dev.c:924: error: expected ‘)’ before ‘UTS_RELEASE’
make[2]: *** [dmx_dev.o] Error 1
make[2]: Leaving directory `/home/nkwai/dmx4linux-2.5/drivers/dmxdev'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/nkwai/dmx4linux-2.5/drivers'
make: *** [all] Error 2

```

---

### Post by Mr. C. on 2007-07-14
This is no longer a configure error (as per the subject), but how do I build a kernel or kernel modules.

And the error has not changed.  What error do you see first?  That is the one to focus on.

MrC

---

### Post by dangermouse28 on 2007-09-18
Has anyone managed to get dmx4linux installed and working?

---

