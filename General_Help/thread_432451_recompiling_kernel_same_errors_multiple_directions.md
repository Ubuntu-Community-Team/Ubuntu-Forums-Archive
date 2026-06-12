---
title: "recompiling kernel same errors multiple directions"
date: 2007-05-04
forum: General Help
---

### Post by me113114 on 2007-05-04
I'm having troubles recompiling the 2.6.20.15-generic kernel.  It doesn't matter what I try I seem to be getting the same error over and over.

I do this:
ln -s /usr/src/linux-headers-2.6.20.15-generic /usr/src/linux
make menuconfig 

I go through and uncheck all the obvious unnecessaries like scsi support and wan support
then I ran

make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

and get this error:

====== making target debian/stamp-build-kernel [new prereqs: sanity_check stamp-kernel-conf]======
This is kernel package version 10.065ubuntu5.
/usr/bin/make  EXTRAVERSION=-15-generic-custom  ARCH=i386 \
                             bzImage
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [debian/stamp-build-kernel] Error 2

so I've been instructed by several how-to's to do 'make-kpkg clean' and get this error:

====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=i386 distclean
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.20-15-generic/drivers/infiniband/hw/amso1100/Makefile: No such file or directory
make[5]: *** No rule to make target `/usr/src/linux-headers-2.6.20-15-generic/drivers/infiniband/hw/amso1100/Makefile'.  Stop.
make[4]: *** [drivers/infiniband/hw/amso1100] Error 2
make[3]: *** [drivers/infiniband] Error 2
make[2]: *** [_clean_drivers] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [real_stamp_clean] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [CLN-common] Error 2

This error has occured with the 2.6.20.15, 2.6.20.15-generic, 2.6.21.1 kernels and keep getting the same exact errors.  Any help will be appreciated!!!

Darren

---

### Post by me113114 on 2007-05-04
nevermind I figured it out.  found that I didn't have the linux-source package installed.  Installed that and fixed my problem.  kernel is now being compiled.

---

