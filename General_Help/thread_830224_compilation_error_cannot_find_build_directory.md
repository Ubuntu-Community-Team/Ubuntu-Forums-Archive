---
title: "compilation error cannot find build directory"
date: 2008-06-15
forum: General Help
---

### Post by Gatemaze on 2008-06-15
Hi,

I am getting an error that the build directory does not exist:
make[1]: Entering directory `/lib/modules/2.6.15-51-386/build'
make[1]: *** No rule to make target `for'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-51-386/build'
make: *** [default] Error 2

and it actually does not exist. I have installed the kernel source.... Can someone give me some light on what to do? Thanks.

---

### Post by Gatemaze on 2008-06-15
Partially resolved by making a symbolic link to the source directory.

ln -sf /usr/src/linux-source-2.6.15/ /lib/modules/2.6.15-51-386/build

Still getting compilation errors though:
make -C /lib/modules/2.6.15-51-386/build -I/lib/modules/2.6.15-51-386/build/drivers/usb/serial SUBDIRS=/home/gats/PhDProgramming/Modules/Real_Robots/SICK_LMS200/driver for serial to usb/utm1925 adapter/mos7715-2.6-1.0.4 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.15'
Makefile:490: .config: No such file or directory
make[1]: *** No rule to make target `for'. Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [default] Error 2

---

### Post by Gatemaze on 2008-06-15
And I have reached the following stage:

make -C /lib/modules/2.6.15-51-386/build -I/lib/modules/2.6.15-51-386/build/drivers/usb/serial SUBDIRS=/home/gats/Desktop/mos7715-2.6-1.0.4 modules
make[1]: Entering directory `/lib/modules/2.6.15-51-386/build'

WARNING: Symbol version dump /lib/modules/2.6.15-51-386/build/Module.symvers
is missing; modules will have no dependencies and modversions.

CC [M] /home/gats/Desktop/mos7715-2.6-1.0.4/mos7715.o
/home/gats/Desktop/mos7715-2.6-1.0.4/mos7715.c:41:27: error: linux/version.h: No such file or directory
In file included from include/linux/fs.h:11,
from include/linux/tty.h:20,
from /home/gats/Desktop/mos7715-2.6-1.0.4/mos7715.c:42:
include/linux/ioctl.h:4:23: error: asm/ioctl.h: No such file or directory
In file included from include/linux/posix_types.h:47,
from include/linux/types.h:14,
from include/linux/rcuref.h:35,
from include/linux/fs.h:12,
from include/linux/tty.h:20,
from /home/gats/Desktop/mos7715-2.6-1.0.4/mos7715.c:42:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/asm/posix_types.h:13:22: error: features.h: No such file or directory
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/asm/posix_types.h:14:35: error: no include path in which to search for asm/posix_types.h
In file included from include/linux/rcuref.h:35,
from include/linux/fs.h:12,
from include/linux/tty.h:20,
from /home/gats/Desktop/mos7715-2.6-1.0.4/mos7715.c:42:
include/linux/types.h:15:23: error: asm/types.h: No such file or directory
In file included from include/linux/rcuref.h:35,
from include/linux/fs.h:12,
from include/linux/tty.h:20,
from /home/gats/Desktop/mos7715-2.6-1.0.4/mos7715.c:42:





With many more lines and all sort of errors until compilation fails.... Any help? Thanks.

---

