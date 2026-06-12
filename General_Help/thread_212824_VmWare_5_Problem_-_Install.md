---
title: "VmWare 5 Problem - Install"
date: 2006-07-10
forum: General Help
---

### Post by Hellaxe on 2006-07-10
Hi people:
I'm having this problem when i run the runme.pl script from the vmware-any-any-update101. I even tried the 95 but the result is the same:```
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-686'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
gcc: installation problem, cannot exec 'cc1plus': No such file or directory
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-686'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I'm stuck here. Can anybody help me??

Thanks.

PS: By the way it worked fine in Breezy.

---

### Post by Hellaxe on 2006-07-11
For those who's interested in knowing i've made a solution to this problem.

I had to install the g++-4.0 package to make it work.

See ya

---

