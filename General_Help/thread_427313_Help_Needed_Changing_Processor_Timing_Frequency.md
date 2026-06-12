---
title: "Help Needed Changing Processor Timing Frequency"
date: 2007-04-29
forum: General Help
---

### Post by nullfactor on 2007-04-29
I want to use the Rosegarden sequencer package.  When I installed it, it said my processor timing frequency was set too low.  Checking the kernel configuration, the frequency is set to 250Hz.  I want to set it to 1000Hz.  However, when I do a menuconfig and try to recompile the kernel, I get errors:

make-kpkg clean:
```
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean 

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
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
```

make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image:
```
exec debian/rules  DEBIAN_REVISION=386  INITRD=YES  kernel_image kernel_headers modules_image 

====== making target CONFIG-common [new prereqs: testdir]======

====== making target CONFIG-common [new prereqs: stamp-conf]======
This is kernel package version 10.065ubuntu5.
====== making stamp-arch-conf because of  ======

====== making target CONFIG-arch [new prereqs: stamp-arch-conf]======
====== making conf.vars because of .config ======

====== making target CONFIG-arch [new prereqs: .config conf.vars]======
This is kernel package version 10.065ubuntu5.
====== making target CONFIG/linux-headers-2.6.20-15-generic [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-image-2.6.20-15-generic [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-uml-2.6.20-15-generic [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-xen0-2.6.20-15-generic [new prereqs: CONFIG-arch]======

====== making target CONFIG/linux-xenu-2.6.20-15-generic [new prereqs: CONFIG-arch]======

====== making stamp-configure-arch because of  ======
====== making target configure-arch [new prereqs: stamp-configure-arch]======
====== making stamp-indep-conf because of  ======

====== making target CONFIG-indep [new prereqs: stamp-indep-conf]======
====== making target CONFIG-indep [new prereqs: conf.vars stamp-kernel-conf]======
This is kernel package version 10.065ubuntu5.
====== making target CONFIG/linux-source-2.6.20-15-generic [new prereqs: CONFIG-indep]======

====== making target CONFIG/linux-doc-2.6.20-15-generic [new prereqs: CONFIG-indep]======

====== making target CONFIG/linux-manual-2.6.20-15-generic [new prereqs: CONFIG-indep]======

====== making stamp-configure-indep because of  ======
====== making target configure-indep [new prereqs: stamp-configure-indep]======
====== making stamp-configure because of  ======
====== making target debian/stamp-build-kernel [new prereqs: sanity_check stamp-kernel-conf]======
This is kernel package version 10.065ubuntu5.
/usr/bin/make    ARCH=i386 \
                             bzImage
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [debian/stamp-build-kernel] Error 2

```

I attempted to follow the instructions found on [http://ubuntuforums.org/showthread.php?t-311158](http://ubuntuforums.org/showthread.php?t-311158) but succeeded in blowing up my sound, network, and USB capabilities.  Any help would be appreciated.

Oh, for the record, I am using 2.6.20-15-generic.

Thanks!

---

### Post by nullfactor on 2007-04-29
Anybody have any ideas on this?  Thanks.:confused:

---

### Post by nullfactor on 2007-04-30
bump... still need a hand.   thanx!

---

### Post by Hendrixski on 2007-05-06
apt-get install linux-lowlatency

I've heard good thigns about it, it should have a higher rate

---

