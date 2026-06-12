---
title: "Problem installing vmware &quot;cant compile vmmon&quot; something to do with headers ?"
date: 2007-03-14
forum: General Help
---

### Post by BodleyTunes on 2007-03-14
This is my version of Linux:

```
root@linuxweb1:/shares/public/vmware-server-distrib# dpkg -l | grep 2.6.20-8
ii  linux-headers-2.6.20-8           2.6.20-8.14                            Header files related to Linux kernel version
ii  linux-headers-2.6.20-8-generic   2.6.20-8.14                            Linux kernel headers for version 2.6.20 on x
ii  linux-image-2.6.20-8-generic     2.6.20-8.14                            Linux kernel image for version 2.6.20 on x86
root@linuxweb1:/shares/public/vmware-server-distrib#
root@linuxweb1:/shares/public/vmware-server-distrib# uname -r
2.6.20-8-generic

```

Getting this error when I try to install vmware:

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)?
```

I got this working with 6.06 but I can't remember what I did!  Stupid me!  Not sure if its even harder to get working with feisty though.

Can anyone help me?

Thankyou.

Jonathan.

---

### Post by teaker1s on 2007-03-14
```
sudo apt-get install build-essential
```
```
sudo apt-get install linux-headers-`uname -r`
 sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
```

---

### Post by BodleyTunes on 2007-03-14
Thanks the for the quick reply dude!

okies, done that now, had to create a dir called "build" though as it said it didnt exist.

Now do I just run the vmware install again?

ps: the /build dir contains some directories, one is blue and one is red (using ls to list them)

---

### Post by BodleyTunes on 2007-03-14
do i point vmware to use the directory i just created ??

---

### Post by BodleyTunes on 2007-03-14
OK still no worky :'(

Same output as before as far as I can see :( 

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-8-generic/build/include] /build/2.6.20-8-generic/build/include

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /build/2.6.20-8-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-8-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:80:
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â...â before âcompat_exitâ
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or â...â before âexit_codeâ
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to âintâ in declaration of â_syscall1â
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-8-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Have I pointed it to the right place ??

---

### Post by teaker1s on 2007-03-14
I'm sorry I do not know the answer, I purely thought you had a common compiling error,have you googled the error?

---

### Post by BodleyTunes on 2007-03-15
Thanks for your help :)

I ended up solving it lastnight, it was quite simple reallly, I just did this:

> 1. Download and install the latest vmware-any-any patch (unsupported) from the following website: [http://platan.vc.cvut.cz/ftp/pub/vmware/](http://platan.vc.cvut.cz/ftp/pub/vmware/)
-to install, extract the tarball to the Ubuntu Linux host in a temporary directory, and run ./runme.pl as sudo or root. 
-failure to follow step 1 will result in an unsuccessful vmware-config.pl (complaints of missing vmmon kernel modules and the inability to find "make") 

2. Follow the instructions for VMware Workstation on Ubuntu Linux host at this website: [https://wiki.ubuntu.com/VmWare](https://wiki.ubuntu.com/VmWare)

Many thanks,

Jonathan.

---

