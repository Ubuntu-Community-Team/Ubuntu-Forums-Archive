---
title: "error compilation kernel module not finding the include files"
date: 2017-05-21
forum: General Help
---

### Post by sblu23 on 2017-05-21
Folks,

I created a simple 'hello world' kind of a driver and having trouble compiling.  

here's the [COLOR=#ff0000]**error**[/COLOR]
```

~/Kernel/linux-joule-4.4.0$ sudo make -C ~/Kernel/linux-joule-4.4.0/kernel M='pwd' modulemake: Entering directory '/home/Kernel/linux-joule-4.4.0/kernel'
cc     module.c   -o module
**[COLOR=#ff0000]module.c:19:26: fatal error: linux/export.h: No such file or directory[/COLOR]**
compilation terminated.
<builtin>: recipe for target 'module' failed
make: *** [module] Error 1
make: Leaving directory '/home/Kernel/linux-joule-4.4.0/kernel'

```

on my installation, the kernel source module.c is located here:
**./kernel/module.c**
export.h is here:[B]
./include/linux/export.h[/B]

How do I do a global correction for the location of the include file short of editing a bunch of the kernel c files?

Thanks!

---

### Post by steeldriver on 2017-05-22
Have a look here:

[How to include local header files in linux kernel module]("https://unix.stackexchange.com/a/18165/65304")

Also, there should be no need to use `sudo`

---

### Post by sblu23 on 2017-05-25
Hi @steeldriver
the problem is that these are not 'my' include files.  these include files are from the kernel source and are visible in the kernel tree.  I don't have any include files for my module yet.

---

### Post by steeldriver on 2017-05-25
So how did you obtain the contents of your ~/Kernel/linux-joule-4.4.0/kernel directory? Does it contain the relevant kernel headers (i.e. the stuff that would be provided by the linux-headers package in a normal in-tree build)?

---

### Post by sblu23 on 2017-05-25
yes it does, as I showed in my original post, the .h files are there; the build system is not finding it...

---

### Post by sblu23 on 2017-05-25
i obtained the kernel source following the direction at this link
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)
and was able to successfully compile the kernel (.deb) file.

---

### Post by sblu23 on 2017-05-25
found the issue, i simply needed to put the entire include path in my source file.  now i'm having another issue, but will resubmit another thread for that one.

---

