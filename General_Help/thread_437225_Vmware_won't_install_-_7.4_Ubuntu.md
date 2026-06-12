---
title: "Vmware won't install - 7.4 Ubuntu"
date: 2007-05-08
forum: General Help
---

### Post by alexjhill on 2007-05-08
I looked in threads saw the "Vmware-any-any" fix for new kernel's but i get this error... Help! 



Using newest Vmware - trial version . I ran the update to the vmware-config.pl with .....



alex@Laptop-AH:~/vmware-any-any-update109$ sudo ./runme.pl

Updating /usr/bin/vmware-config.pl ... already patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.


This is the output............................





Building the vmmon module.

Building for VMware Workstation 5.5.0 or 5.5.1.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
g[COLOR="Red"]cc: error trying to exec 'cc1plus': execvp: No such file or directory[/COLOR]
[COLOR="Red"]make[2]: *** [/tmp/vmware-config0/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.[/COLOR]

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

---

