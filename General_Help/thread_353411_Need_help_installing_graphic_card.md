---
title: "Need help installing graphic card"
date: 2007-02-04
forum: General Help
---

### Post by xtimmyx on 2007-02-04
I am trying to install drivers for my friends integrated 82865G Intel grapic card but we cant make it work. 

When i download it from the Intel site and try to install it in the termial i get the error:

Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


HERE IS THE LOG:

make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/hakan/Desktop/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/hakan/Desktop/dripkg/agpgart-2.0/backend.o
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:281: warning: ‘inter_module_register’ is deprecated (declared at include/linux/module.h:562)
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/hakan/Desktop/dripkg/agpgart-2.0/backend.c:301: warning: ‘inter_module_unregister’ is deprecated (declared at include/linux/module.h:563)
make[2]: *** [/home/hakan/Desktop/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/hakan/Desktop/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/hakan/Desktop/dripkg/drm'
make -C /lib/modules/2.6.17-10-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
rm: cannot remove `/home/hakan/Desktop/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/hakan/Desktop/dripkg/drm'
make: *** [gdg.ko] Error 2




I have also tried with this guide: [http://wiki.linuxquestions.org/wiki/Installing_intel-82865G_drivers](http://wiki.linuxquestions.org/wiki/Installing_intel-82865G_drivers)
But when i run the run the make command i get the following errors:

root@hakan-desktop:/home/hakan/Desktop/xc# make World
./config/util/printver.c:10:19: error: stdio.h: No such file or directory
./config/util/printver.c:11:20: error: stdlib.h: No such file or directory
./config/util/printver.c: In function ‘main’:
./config/util/printver.c:19: warning: incompatible implicit declaration of built-in function ‘printf’
./config/util/printver.c:27: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [World] Error 1

Can anyone help me? It would really save my day, thanks.

---

### Post by pay on 2007-02-04
I thought that Edgy already had this driver built in:confused: ohwell, try```
glxinfo | grep rendering
```And how many fps do you get from```
glxgears
```Also add```
Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```to /etc/X11/xorg.conf (which will only work if the driver is built in). Also try ```
sudo aptitude install build-essential
```before compiling.

---

