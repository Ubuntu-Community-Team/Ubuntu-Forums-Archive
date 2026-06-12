---
title: "Error building kernel module"
date: 2007-06-08
forum: General Help
---

### Post by wtavares on 2007-06-08
Hi,

I am trying to compile the following code:

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
  return 0;
}

```

When building I got the following errors:
error: linux/init.h: No such file or directory
error: linux/module.h: No such file or directory

I (think) have all needed packages installed as build-esentials, gcc, libraries, etc...

I've tried on both Ubuntu 6.10 and 7.04.

Other C/C++ code in userspace works fine.

Thanks.

---

### Post by yabbadabbadont on 2007-06-08
How about the linux-headers for your running kernel?

---

### Post by wtavares on 2007-06-08
Nope. I  already have them installed...
linux-headers-2.6.20-16-generic (for Feisty Fawn)

---

### Post by yabbadabbadont on 2007-06-08
```
/home/daffy/temp $ aptitude search linux-headers | grep ^i
i   linux-headers-2.6.20-16         - Header files related to Linux kernel versi
i   linux-headers-2.6.20-16-generic - Linux kernel headers for version 2.6.20 on
i   linux-headers-generic           - Generic Linux kernel headers              
/home/daffy/temp $ ls /usr/include/linux/in*
/usr/include/linux/in.h   /usr/include/linux/in_route.h   /usr/include/linux/inotify.h
/usr/include/linux/in6.h  /usr/include/linux/inet_diag.h  /usr/include/linux/input.h
/home/daffy/temp $ ls /usr/include/linux/m*
/usr/include/linux/magic.h      /usr/include/linux/meye.h      /usr/include/linux/mmtimer.h   /usr/include/linux/msg.h
/usr/include/linux/major.h      /usr/include/linux/mii.h       /usr/include/linux/mqueue.h    /usr/include/linux/mtio.h
/usr/include/linux/matroxfb.h   /usr/include/linux/minix_fs.h  /usr/include/linux/mroute.h
/usr/include/linux/mempolicy.h  /usr/include/linux/mman.h      /usr/include/linux/msdos_fs.h

```
Looks like those header files don't exist....  are you sure that you are using the correct names?

---

### Post by yabbadabbadont on 2007-06-08
Found them.  /lib/modules/`uname -r`/build/include is the correct include path to specify to gcc with -I.  But that just leads to a whole slew of other errors.  I think we both need to find a tutorial somewhere on the proper way to build a module.  :D

---

### Post by wtavares on 2007-06-08
You're right. I've already try to include this path in gcc command line. I got a bunch of error messages.

I did that in the past with a simple command like "gcc module.c". I'm not sure but I think that was on a Suse. The sample file was extracted from "linux device drivers. Third Edition"

---

### Post by yabbadabbadont on 2007-06-08
Maybe that book is for a 2.4 kernel?  You might try installing the kernel sources and then looking through some of that code to see how a 2.6 module is designed.  Some of the module code is pretty small, so that it shouldn't be too difficult to understand.  I'm not sure where it is in the source tree but, from past experience, I know that kbtab.c is pretty small.

---

### Post by wtavares on 2007-06-08
The book claims that it is compatible with kernel 2.6.10 and above. Anyway, I'll take a closer look into your suggested file.

---

### Post by wtavares on 2007-06-08
After some research I found the right way. 
First, the book is wrong. It doesn't cover the 2.6 kernel.

This is the complete code. I forgot the two last lines in the first post:

hello.c
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

I also used a makefile

Makefile
```

ifneq ($(KERNELRELEASE),)
    obj-m       := mhello.o

    else
    KDIR        := /lib/modules/$(shell uname -r)/build
    PWD         := $(shell pwd)

    default:
        $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
    endif

```

To build the module I've used the following command:
```

make -C /usr/src/linux M=/home/wtavares/teste/ modules

```

And everything works fine.

You can install the module and remove it with the following commands:
```

sudo insmod mhello.ko
sudo rmmod mhello.ko

```

Check the generated messages with:
```

sudo dmesg

```

---

### Post by yabbadabbadont on 2007-06-08
Thanks for sharing.  Glad you figured it out.

---

