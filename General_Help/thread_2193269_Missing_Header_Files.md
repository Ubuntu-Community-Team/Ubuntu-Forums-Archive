---
title: "Missing Header Files"
date: 2013-12-12
forum: General Help
---

### Post by Ashiq_Irphan on 2013-12-12
I`m trying to compile a program actually meant for OS with Kernel 2.4.
I`m in the process of making changes in order to make it possible to run on Ubuntu 12.04. 

When I try to *make*, I get the following error

```
In file included from /lib/modules/3.8.0-29-generic/build/include/linux/types.h:5:0,
                 from /lib/modules/3.8.0-29-generic/build/include/linux/list.h:4,
                 from /lib/modules/3.8.0-29-generic/build/include/linux/module.h:9,
                 from kaodv-mod.c:30:
/lib/modules/3.8.0-29-generic/build/include/uapi/linux/types.h:4:23: fatal error: asm/types.h: No such file or directory
compilation terminated.
``` 

So I checked my kernel directory and was not able to find a folder names *asm*, but I did find a folder named [I]asm-generic

[/I]```
/usr/src/linux-headers-3.8.0-29-generic/include/asm-generic
```
I tried creating a symbolic link 

```
root@vm1-VirtualBox:~# mkdir /usr/src/linux-headers-3.8.0-29-generic/include/asm
root@vm1-VirtualBox:~# ln -s /usr/src/linux-headers-3.8.0-29-generic/include/asm-generic/* /usr/src/linux-headers-3.8.0-29-generic/include/asm

```

But I still get the same error. All suggestions are welcomed, Thanks in advance.
[I]
P.S: I`m not sure if asm and asm-generic are same or not.

I missed an important information, the only types.h file I found was

```
[/I]/usr/src/linux-headers-3.8.0-29-generic/include/linux/types.h[I]
```

Is it okay to use this file ?

**Other Informations**
[/I]OS: Ubuntu 12.04
Kernel Version: 3.8.0-29 
  Program I`m trying to compile:[http://sourceforge.net/projects/aodvuu/](http://sourceforge.net/projects/aodvuu/)

---

