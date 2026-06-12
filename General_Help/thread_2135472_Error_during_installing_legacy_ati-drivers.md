---
title: "Error during installing legacy ati-drivers"
date: 2013-04-14
forum: General Help
---

### Post by vinxtreme on 2013-04-14
hi,
    Since my laptop has ATI Readon 4000 series graphic card, I first had to install Opencsource xserver-xorg-video-ati driver but the laptop wont cool down and 'sensors' show radeon pci temperatures around 80 degrees.So had now tried to install legacy drivers first flgrx-legacy but catalyst center wont openup and temperature wont fall, now  as suggested by this link
 [HTML]http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide[/HTML] 
i tried installing legacy drivers from ati site [http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/12-6/amd-driver-installer-12.6-legacy-x86.x86_64.zip).
But during installation i get this error.

```
....
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/fglrx/8.970/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.970-0ubuntu1) ...
Setting up fglrx-dev (2:8.970-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```

Installed linux-headers-generic as some posts suggested (related to same error but in some other installation) but to no avail ...


make.log contains 
```
DKMS make.log for fglrx-8.970 for kernel 3.5.0-23-generic (x86_64)
Mon Apr 15 18:50:51 IST 2013
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.5.0-23-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.970/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-23-generic'
  CC [M]  /var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.c: In function &#8216;KCL_MEM_AllocLinearAddrInterval&#8217;:
/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.c:2152:5: error: implicit declaration of function &#8216;do_mmap&#8217; [-Werror=implicit-function-declaration]
/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.c:2152:13: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/fglrx/8.970/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.970/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-23-generic'
make: *** [kmod_build] Error 2
build failed with return value 2

```


Thanks in advance.

---

### Post by vinxtreme on 2013-04-14
:).....
followed this [HTML] http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Alternative_Manual_Installation[/HTML]
and the GUI install poped up in which option text was missing, after hitting different option buttons (trial and error) it got through.

But now sensors won't show radeon-pic adaptor temperature
tried 
```
aticonfig --odgt
aticonfg --odfc 
```

returns
```
ERROR - Get temperature failed for the Default Adapter - ATI Mobility Radeon HD 4500/5100 Series
```

---

