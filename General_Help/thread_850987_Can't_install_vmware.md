---
title: "Can't install vmware"
date: 2008-07-06
forum: General Help
---

### Post by POW R TOC H on 2008-07-06
I can't install vmware. I have tried experimenting and google-ing but everything failed.
This is what I did (my kernel is 2.6.24-16-generic):
First I tried running vmware-install.pl as usual, but it said it doesn't have an appropriate module for my kernel. So I told it to compile one :)

At first I let it use it's default path for kernel headers, but when that failed, I entered both
```

/usr/src/linux-headers-2.6.24-16-generic/
and
/usr/src/linux-headers-2.6.24-16-generic/include

```
but none worked.
I have tried with vmware-any-any-update115 but that failed too.
The error I get every time is this :
```

VMware 2 or VMware Express detected, building for VMware 2, VMware Express and VMware Workstation 4.0.x.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /usr/src/linux-headers-2.6.24-16-generic/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config3/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config3/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Any ideas as to why this happens and how to fix it?
What should I do (I'm still rather new to linux, so forgive my ignorance)
Thank you in advance.

---

### Post by kuja on 2008-07-06
I would try this: [http://communities.vmware.com/thread/26693](http://communities.vmware.com/thread/26693)

---

### Post by POW R TOC H on 2008-07-06
Done that. It did compile (with vmware-any-any-116) but now when I try to run a virtual machine I get this error :( :
```

Version mismatch with vmmon module: expecting 167.0, got 137.0.
You have an incorrect version of the `vmmon' kernel module.
Try reinstalling VMware Workstation.

```
```
Failed to initialize monitor device.
```
```
Unable to change virtual machine power state: Cannot find a valid peer process to connect to.
```
```
Failed to reply to the dialog: Pipe: Read failed
```
The version of my vmware workstation is 6.0.2 build-59824

---

