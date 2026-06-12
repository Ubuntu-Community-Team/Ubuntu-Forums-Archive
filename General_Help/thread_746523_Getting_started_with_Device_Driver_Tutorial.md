---
title: "Getting started with Device Driver Tutorial"
date: 2008-04-05
forum: General Help
---

### Post by reg2117 on 2008-04-05
Ubuntu Forums,
    I am trying to follow a simple tutorial for writing device drivers at the following link:
[http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0](http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0)

The first step in the tutorial is to write and compile a very simple module that does nothing but introduces the idea of inserting and removing modules into the kernel. 

Following the tutorial, I have created the file "nothing.c" as follows
```

#include <linux/module.h>

MODULE_LICENSE("Dual BSD/GPL");
```

and the following makefile:
```

obj-m := nothing.o
```

The tutorial suggests to compile the file with the following command:
$ make -C /usr/src/kernel-source-2.6.8 M=pwd modules

My machine is running Ubuntu Fiesty and the above directory does not exist.
There is a directory /usr/src/linux-headers-2.6.20-16-generic/include/linux with the file module.h.

When I run the command:
$ make -C /usr/src/linux-headers-2.6.20-16-generic/include/ M=pwd modules

I get the following:
make: Entering directory `/usr/src/linux-headers-2.6.20-16-generic/include'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic/include'

Any help getting this first module to compile would be very much appreciated.

Thanks!

---

### Post by nick_h on 2008-04-05
This is an advanced topic.  I think your guide assumes that you already know how to install the kernel source and compile kernels.

If you want to know how to install and compile a kernel read - [Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).

The [Master Kernel](http://ubuntuforums.org/showthread.php?t=311158) thread is also worth reading.

There is an online book published by O'Reilly called [Linux Device Drivers](http://www.xml.com/ldd/chapter/book/).

There is also a good introduction to Kernel hacking at the [linuxchix](http://www.linuxchix.org/content/courses/kernel_hacking/) site.  ( chapter 8 ).

---

### Post by reg2117 on 2008-04-06
Thank you for the views and the reply.
To my relief, the link [[COLOR="Blue"]Kernel/Compile[/COLOR]]("https://help.ubuntu.com/community/Kernel/Compile") is explicit in stating compiling a special driver is NOT a reason for compiling the kernel.

But the above link did lead to some new search keywords which led me to the following tutorial:
[[COLOR="Blue"]/dev/hello_world: A Simple Introduction to Device Drivers under Linux[/COLOR]]("http://www.linuxdevcenter.com/pub/a/linux/2007/07/05/devhelloworld-a-simple-introduction-to-device-drivers-under-linux.html?page=1")

Following the tutorial, I installed the module-assistant package by:

```
$ sudo apt-get install module-assistant
```

and then rewrote the makefile as per the tutorial:
```
# obj-m is a list of what kernel modules to build.  The .o and other
# objects will be automatically built from the corresponding .c file -
# no need to list the source files explicitly.

obj-m := hello.o 

# KDIR is the location of the kernel source.  The current standard is
# to link to the associated source tree from the directory containing
# the compiled modules.
KDIR  := /lib/modules/$(shell uname -r)/build

# PWD is the current working directory and the location of our module
# source files.
PWD   := $(shell pwd)

# default is the default make target.  The rule here says to run make
# with a working directory of the directory containing the kernel
# source and compile only the modules in the PWD (local) directory.
default:
	$(MAKE) -C $(KDIR) M=$(PWD) modules

```

This compiled successfully. And I was able to insert and remove the module into the kernel. So making progress (ie knowing just enough to be truly dangerous)!!

Future threads will be posted to the [[COLOR="Blue"]Programming Talk[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=39") board.

Thanks again!

---

