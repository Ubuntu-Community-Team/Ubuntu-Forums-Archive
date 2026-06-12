---
title: "Configure warnings on GCC cross-compiler build"
date: 2020-09-24
forum: General Help
---

### Post by xvilhelm on 2020-09-24
I'm trying to build a gcc cross-compiler from source, and whenever i invoke make it results in an error. I'd appreciate any help!

my versions:
```
Ubuntu 18.04.3 LTS
gcc-7.5.0
autoconf-2.69
```

```
./confiigure options
--target=arm-none-eabi
--prefix=/usr/bin/crossbuild
--without-headers
--enable-multilib
--with-multilib=armv7e-m
--with-gnu-as
--with-gnu-ld
--with-dwarf2
--with-newlib
--with-system-zlib
--without-libffi
--disable-decimal-float
--disable-nls
--enable-languages="c,c++"
--enable-interwork
--disable-libstdcxx-pch 
--with-newlib


make all
configure: WARNING: No native atomic operations are provided for this platform.
configure: WARNING: They cannot be faked when thread support is disabled.
configure: WARNING: Thread-safety of certain classes is not guaranteed.
.
.
.
configure: WARNING: stdbool.h: present but cannot be compiled
configure: WARNING: stdbool.h:     check for missing prerequisite headers?
configure: WARNING: stdbool.h: see the Autoconf documentation
configure: WARNING: stdbool.h:     section "Present But Cannot Be Compiled"
configure: WARNING: stdbool.h: proceeding with the compiler's result
checking for stdbool.h... no
checking stdalign.h usability... no
checking stdalign.h presence... yes
configure: WARNING: stdalign.h: present but cannot be compiled
configure: WARNING: stdalign.h:     check for missing prerequisite headers?
configure: WARNING: stdalign.h: see the Autoconf documentation
configure: WARNING: stdalign.h:     section "Present But Cannot Be Compiled"
configure: WARNING: stdalign.h: proceeding with the compiler's result
checking for stdalign.h... no
checking for the value of EOF... configure: error: computing EOF failed
Makefile:10307: recipe for target 'configure-target-libstdc++-v3' failed
make[1]: *** [configure-target-libstdc++-v3] Error 1
make[1]: Leaving directory '/home/metaw1ll/crossbuild/tivac/gcc'
Makefile:889: recipe for target 'all' failed
make: *** [all] Error 2

```

---

