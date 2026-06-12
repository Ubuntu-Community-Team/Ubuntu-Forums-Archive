---
title: "Gcc errors when installing VMware Server"
date: 2007-02-17
forum: General Help
---

### Post by ephesius on 2007-02-17
Im trying to install VMware server and everytime I get this error:


Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config9/vmmon-only'
make -C /lib/modules/2.6.17-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
/tmp/vmware-config9/vmmon-only/Makefile:89: *** Inappropriate build environment: you wanted to use gcc version 4.1.2 while kernel attempts to use gcc version 3.4.6.
/tmp/vmware-config9/vmmon-only/Makefile:91: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.1.  Stop.
make[1]: *** [_module_/tmp/vmware-config9/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config9/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



Anyone have any ideas i tried doing this:
  ```
export CC=/usr/bin/gcc-4.1
```
but no dice. I cant figure out what the problem is any help would be awesome thanks.

---

### Post by ephesius on 2007-02-20
Ok, I am an idiot. This was really simple when i actually sat down and looked at it.

```
sudo rm /usr/bin/gcc
```
```
sudo ln -s /usr/bin/gcc-4.1
```

Thats what had to be done in case anyone else had this "problem".

---

