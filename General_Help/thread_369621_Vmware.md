---
title: "Vmware"
date: 2007-02-24
forum: General Help
---

### Post by tempest130 on 2007-02-24
Hi everybody,

I hoping someone could help me with this.  I've been trying to install VMWARE WORKSTAION on my Ubuntu 6.10 laptop.  However I get the following error:


Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /usr/src/linux-headers-2.6.17-11-generic/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:62: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config2/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Could anyone PLEASE help me with this.  Thanks.

Sean

---

### Post by cronholio on 2007-02-25
```
cd /usr/lib/vmware/modules/source
tar xf vmmon.tar
tar xf vmnet.tar
vim vmmon-only/Makefile.kernel #Add -DKBUILD_BASENAME=\\"$(DRIVER)\\" just after -Iinclude2/asm/mach-default (on the same line use a \ to indicate the new line should be ignored).
vim vmnet-only/Makefile.kernel #Add -DKBUILD_BASENAME=\\"$(DRIVER)\\" just after -Iinclude2/asm/mach-default (on the same line use a \ to indicate the new line should be ignored).
mv vmmon.tar vmmon.tar.save
mv vmnet.tar vmnet.tar.save
tar cf vmmon.tar vmmon-only
tar cf vmnet.tar vmnet-only
```

From [here.]("http://www.cuberick.com/?p=48")

---

