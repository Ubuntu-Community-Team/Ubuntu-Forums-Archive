---
title: "VMWare doesn't like me"
date: 2005-05-27
forum: General Help
---

### Post by djpinger on 2005-05-27
I am trying to install vmware 5.0, and I get the following:

```

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /usr/src/linux-headers-2.6.10-5-386/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:45:
/tmp/vmware-config3/vmmon-only/linux/driver.h:68:1: warning: "DEVICE_NAME_SIZE" redefined
In file included from include/linux/miscdevice.h:5,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:12,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:45:
include/linux/device.h:25:1: warning: this is the location of the previous definition
objdump: /tmp/vmware-config3/vmmon-only/linux/.tmp_driver.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config3/vmmon-only/linux/hostif.c:57:
/tmp/vmware-config3/vmmon-only/linux/driver.h:68:1: warning: "DEVICE_NAME_SIZE" redefined
In file included from include/linux/miscdevice.h:5,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:12,
                 from /tmp/vmware-config3/vmmon-only/linux/hostif.c:57:
include/linux/device.h:25:1: warning: this is the location of the previous definition
objdump: /tmp/vmware-config3/vmmon-only/linux/.tmp_hostif.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
objdump: /tmp/vmware-config3/vmmon-only/common/.tmp_cpuid.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/common/hash.o
objdump: /tmp/vmware-config3/vmmon-only/common/.tmp_hash.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/common/memtrack.o
objdump: /tmp/vmware-config3/vmmon-only/common/.tmp_memtrack.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/common/phystrack.o
objdump: /tmp/vmware-config3/vmmon-only/common/.tmp_phystrack.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/common/task.o
objdump: /tmp/vmware-config3/vmmon-only/common/.tmp_task.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/common/vmx86.o
objdump: /tmp/vmware-config3/vmmon-only/common/.tmp_vmx86.o: File format not recognized
  CC [M]  /tmp/vmware-config3/vmmon-only/vmcore/moduleloop.o
objdump: /tmp/vmware-config3/vmmon-only/vmcore/.tmp_moduleloop.o: File format not recognized
  LD [M]  /tmp/vmware-config3/vmmon-only/vmmon.o
/tmp/vmware-config3/vmmon-only/linux/driver.o: file not recognized: File format not recognized
make[2]: *** [/tmp/vmware-config3/vmmon-only/vmmon.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I have gcc and the linux-headers installed.  Is there anything that I'm doing wrong?

---

### Post by Sgood1971 on 2005-05-27
Try [here](http://www.ubuntuforums.org/showthread.php?t=36873)

---

### Post by Fab on 2005-05-27
[QUOTE=Sgood1971]Try [here](http://www.ubuntuforums.org/showthread.php?t=36873)[/QUOTE]
 i'd also say so
i have the same problem and i posted there already

---

