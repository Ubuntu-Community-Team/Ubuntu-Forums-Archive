---
title: "LInux kernel header files - module.h not found!"
date: 2007-06-03
forum: General Help
---

### Post by ravindra.rajaram on 2007-06-03
I'm new to device drivers on Linux.
the following program when compiled as

 *gcc -c -D__KERNEL__ module1.c*
I get the error:
*module1.c:2:25: error: linux/module.h: No such file or directory*


[I]#define MODULE
#include<linux/module.h>
int init_module(void) { printk("<1>Hello, world\n"); return 0; }
void cleanup_module(void) {printk("<1>GoodBye\n"); }
[/I]


When 'sudo apt-get install linux-headers-`uname -r` 'ed. I get  

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-15-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

What am I missing?


-Ravindra.

---

### Post by thelinuxguy on 2007-06-04
Maybe this makefile will help:
```

obj-m    := module1.o

KDIR    := /lib/modules/$(shell uname -r)/build
PWD    := $(shell pwd)

default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

```

---

### Post by ravindra.rajaram on 2007-06-06
I'm not new to makefiles, but the makefile given above,
I donot see it to be buildinig a module1.o or a module1.ko

do I need to add more content to the makefile.
I tried adding a rule

[I]modules:
            gcc -c -D__KERNEL__  -o module1.o module1.c
[/I]

This does not seem to help build a loadable driver either?


What else am I missing?

-Ravindra.

---

### Post by thelinuxguy on 2007-06-06
Although I have used makefiles, I have never written one myself. So I can't really explain the contents. But if I remember correctly, I have used the above makefile in the past (RedHat system with a 2.6 kernel) since it was in the notes I had made. However, it didn't work at my end this time. Couldn't figure out why.

Anyways, I was able to build a .ko module using the following source, makefile and command. You can find it on pg-24, Chapter 2 (Building and running modules) of the book 'Linux Device Drivers (Third Edition)'.

module1.c
```

#include <linux/init.h>
#include <linux/module.h>

MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
    printk(KERN_ALERT "Hello, world\n");
    return 0;
}

static void hello_exit(void)
{
    printk(KERN_ALERT "Goodbye, cruel world\n");
}

module_init(hello_init);
module_exit(hello_exit);

```

Makefile
```

obj-m    := module1.o

```

Command line
```

make -C /lib/modules/`uname -r`/build  M=`pwd` modules

```

Does it work at your end?

---

### Post by ravindra.rajaram on 2007-06-11
NO!.
It doesn't work yet :(
Although, I've gone through kernel.h on SuSE Linux 9 and I've seen the following steps:

[I]make mrproper
make cloneconfig
make dep
[/I]
and then use  -I/usr/src/`uname -r`/build/include to get the kernel headers in the driver program (apart from using the above make file)
That seemed to have worked with SuSE 9. I'm trying to do the same on UBUNTU.
But met with a blank wall there too! Either the kernel source is incomplete (after all the latest updates!) or I'm making some mistake some where.
I'm going to post another thread to see if some kernel source is missing.

Thanks,
Ravindra.

---

### Post by thelinuxguy on 2007-06-12
What error did you get?

---

### Post by ravindra.rajaram on 2007-06-12
I've posted another thread here:
[http://ubuntuforums.org/showthread.php?t=471329](http://ubuntuforums.org/showthread.php?t=471329)
with the problem.

---

