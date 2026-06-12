---
title: "Installing a new kernel"
date: 2014-01-11
forum: General Help
---

### Post by Purnish_Dave on 2014-01-11
Hi,

I am running 3.8.0-29-generic kernel right now but I want to install and compile a new kernel from source because I am reading a book about the Linux kernel and device driver writing and I require the kernel source so I can build my own modules and insert and remove them using make utility.

My question is when I get the new kernel source and I compile it, then is there any danger that my system will stop working or refuse to boot or something. And will grub offer me a choice on which kernel to boot into? Suppose the new kernel doesn't work, then my system should be unharmed right if the present one works. I've never done this before but I want to learn kernel programming but don't want my machine to become unusable.

Thanks,
P

---

### Post by tgalati4 on 2014-01-11
Yes, you can break your system.  Yes, grub will list your kernel.  During the make process, you will have an opportunity to name your kernel so it will be appended as in "3.8.0-29-my-goofy-kernel".  It's not hard.  It takes two to three hours.  You need some disk space.  Read up on the tutorials. [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Enable the source repositories and download the kernel source.  If you get stuck, do a little searching, then ask here.

A Haiku

Compile the kernel?
A learning experience.
You keep the pieces.

---

### Post by Bucky Ball on 2014-01-11
You don't need to complile it if you don't really want to. The list of kernels will appear at boot and if the new kernel is not working, simply select the old one. That easy. 

This is an example of what is possible:

[https://duckduckgo.com/?q=install+3.12+kernel+12.04](https://duckduckgo.com/?q=install+3.12+kernel+12.04)

You just need to be exact in the kernel you want to install and in what release in your search ...

---

### Post by Purnish_Dave on 2014-01-12
Cool. All I wanted to do was build a simple helloworld.ko module and insert it into the kernel and see it run.
```

#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
    printk(KERN_ALERT "Hello world\n");
    return 0;
}

static void hello_exit(void)
{
    printk(KERN_ALERT "Goodbye world\n");
}

module_init(hello_init);
module_exit(hello_exit);

```

Now I know what I have to do to be able to get a .ko file out of it by running the make command. I have to write a makefile with the line

```

obj-m := helloworld.o

```

Do I have to put the makefile as well as the helloworld.o file in the /usr/src/linux-3.10-x directory ?
How would I compile and make a .ko file out of it?

---

