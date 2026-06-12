---
title: "Kernel Header Files don't match running kernel..."
date: 2007-07-17
forum: General Help
---

### Post by geminias on 2007-07-17
```

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /lib/modules/2.6.20-16-generic/build/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-16-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.


```

Above are the words haunting me.  Someone can shed light?  

Since I personally think I am supplying the header files for my currently running kernel, but I keep getting this message, I'll tell you what I've done.  

```

justin@justin-laptop:~$ uname -a 
Linux justin-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
justin@justin-laptop:~$ cd /usr/src/
justin@justin-laptop:/usr/src$ ls
linux                            linux-headers-2.6.20-16
linux-headers-2.6.20-15          linux-headers-2.6.20-16-generic
linux-headers-2.6.20-15-generic

```

I've tried both the 20-16 versions to no avail.  

module-assistant prepared without errors and when i try the include directory it makes it also fails with the haunting message.  

THANKS FOR ANY HELP!

---

### Post by billguy on 2007-07-19
```

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /lib/modules/2.6.20-16-generic/build/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-16-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.


```

[http://hootbah.co.uk/2006/12/13/vmware-on-debian-etch-kernel-2-6-18-3/](http://hootbah.co.uk/2006/12/13/vmware-on-debian-etch-kernel-2-6-18-3/)

---

