---
title: "VMware workstation instalation problem with gcc compiler"
date: 2008-01-09
forum: General Help
---

### Post by blackwell on 2008-01-09
```
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
gcc: Internal error: Segmentation fault (program cc1plus)
Please submit a full bug report.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.

make[2]: *** [/tmp/vmware-config2/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

ubuntu 7.10 gutsy gibbon 

I tryied

reinstall gcc 
vmware-any-any-update114
vmware-any-any-update115

i got
linux  headers 
gcc 3.3
gcc 3.4
gcc 4.1

any ideas?

---

### Post by taurus on 2008-01-09
Did you install the build-essential package instead of just a gcc compiler?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by blackwell on 2008-01-09
```
 sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by blackwell on 2008-01-09
Any ideas ?

---

