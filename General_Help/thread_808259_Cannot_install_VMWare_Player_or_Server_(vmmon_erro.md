---
title: "Cannot install VMWare Player or Server (vmmon error)"
date: 2008-05-26
forum: General Help
---

### Post by azo313 on 2008-05-26
After I upgraded kernel to 2.6.24-17-generic, VMWare player stopped working. I uninstalled it, and now I get errors trying to re-install it.

The error appears right after this question:

> What is the location of the directory of C header files that match your running kernel? [/lib/modules/2.6.24-17-generic/build/include] 

When I press enter, here is the result:

> Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config2/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config2/vmmon-only/common/vmx86.h:18,
                 from /tmp/vmware-config2/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config2/vmmon-only/common/cpuid.c:14:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config2/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

I've tried several times. I also tried using the vmware-any-any-update117 patch, and it did not help.

I also typed apt-get install gcc build-essential to make sure I have those items.

I'm stuck, and don't know what to do now. I tried both VMWare Player and VMWare Server. Both give the same errors.

---

### Post by azo313 on 2008-05-28
I was never able to solve this issue, so I ended up trying VirtualBox (and I'm very glad I did). I like it better than VMWare. It seems more stable with less issues.

VMWare had better USB support out of the box. VirtualBox took a little extra work to get the USB support working. VirtualBox also has a strange issue that makes printing to a network printer VERY slow. But otherwise, I think it's more user friendly, and more stable. I'm going to stick with VirtualBox going forward.

---

### Post by jimv on 2008-05-28
Hell yeah.  I was using VMWare for awhile, but I couldn't get SUSE to install on it.  Then I switch to VirtualBox and IT ROCKS.

---

