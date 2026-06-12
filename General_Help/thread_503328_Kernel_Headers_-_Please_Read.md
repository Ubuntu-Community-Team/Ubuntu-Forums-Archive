---
title: "Kernel Headers - Please Read"
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

### Post by McNils on 2007-07-17
I think that /usr/src/linux-headers-2.6.20-16-generic/include should work.

---

### Post by geminias on 2007-07-18
I think it should too, but it doesn't.  What do I do?  Go back to windows? lol

---

### Post by pete on 2007-07-19
Did this problem start happening after a kernel upgrade?  If so, you just need to re-run the VMWare install script that you ran when you first installed it.  Just supply all the same answers to the various prompts, and you should be all set.  None of your VM's will be affected.

This is one of the annoyances of VMWare...  any time you update your kernel, you have to re-run the install.

---

