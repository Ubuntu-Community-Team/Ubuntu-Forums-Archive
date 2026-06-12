---
title: "install dazuko on gutsy"
date: 2008-05-29
forum: General Help
---

### Post by cccc on 2008-05-29
hi

I try to install **dazuko** according to:

[http://ubuntuforums.org/showthread.php?t=589911](http://ubuntuforums.org/showthread.php?t=589911)

on my gutsy: but it doesn't work and I get the following errors:```

root@ania:/home/dazuko# uname -a
Linux ania 2.6.22-14-386 #1 Tue Feb 12 07:12:19 UTC 2008 i686 GNU/Linux

root@ania:/home/dazuko# tar xfvz dazuko-2.3.4.tar.gz 
dazuko-2.3.4/
dazuko-2.3.4/README
dazuko-2.3.4/LICENSE.GPL
dazuko-2.3.4/configure
dazuko-2.3.4/dazuko_freebsd.c
dazuko-2.3.4/dazuko_freebsd.h
dazuko-2.3.4/dazuko_linux.c
dazuko-2.3.4/dazuko_linux.h
dazuko-2.3.4/dazuko_platform.h
dazuko-2.3.4/dazukoio_trusted_core.c
dazuko-2.3.4/example_php/
dazuko-2.3.4/example_php/README
dazuko-2.3.4/dazukoio.h
dazuko-2.3.4/dazuko_transport.h
dazuko-2.3.4/dazukoio_dummyos.h
dazuko-2.3.4/dazukoio_core.h
dazuko-2.3.4/example_java/
dazuko-2.3.4/example_java/org/
dazuko-2.3.4/example_java/org/dazuko/
dazuko-2.3.4/example_java/org/dazuko/Dazuko.java
dazuko-2.3.4/example_java/org/dazuko/DazukoAccess.java
dazuko-2.3.4/example_java/README
dazuko-2.3.4/example_java/dazuko_jni.c
dazuko-2.3.4/example_java/org_dazuko_Dazuko.h
dazuko-2.3.4/example_java/Example.java
dazuko-2.3.4/example_c/
dazuko-2.3.4/example_c/example.c
dazuko-2.3.4/example_c/example_mt.c
dazuko-2.3.4/LICENSE.BSD
dazuko-2.3.4/COPYING
dazuko-2.3.4/dazuko_linux26.c
dazuko-2.3.4/dazuko_linux26.h
dazuko-2.3.4/dazuko_call.h
dazuko-2.3.4/dazuko_freebsd5.c
dazuko-2.3.4/dazuko_freebsd5.h
dazuko-2.3.4/dazuko_rsbac.c
dazuko-2.3.4/dazuko_rsbac.h
dazuko-2.3.4/example_perl/
dazuko-2.3.4/example_perl/t/
dazuko-2.3.4/example_perl/t/t01.t
dazuko-2.3.4/example_perl/t/t02.t
dazuko-2.3.4/example_perl/t/t03.t
dazuko-2.3.4/example_perl/t/t04.t
dazuko-2.3.4/example_perl/t/autounblock.inc
dazuko-2.3.4/example_perl/t/t05.t
dazuko-2.3.4/example_perl/Access.pm
dazuko-2.3.4/example_perl/Example.pl
dazuko-2.3.4/example_perl/ExampleOO.pl
dazuko-2.3.4/example_perl/IO.pm
dazuko-2.3.4/example_perl/IO.xs
dazuko-2.3.4/example_perl/Makefile.PL
dazuko-2.3.4/example_perl/Obj.pm
dazuko-2.3.4/example_perl/README
dazuko-2.3.4/example_perl/ExampleThr.pl
dazuko-2.3.4/example_python/
dazuko-2.3.4/example_python/MANIFEST
dazuko-2.3.4/example_python/README
dazuko-2.3.4/example_python/dazukomodule.c
dazuko-2.3.4/example_python/example.py
dazuko-2.3.4/example_python/setup.py
dazuko-2.3.4/dazuko_linux26_lsm.h
dazuko-2.3.4/dazuko_linux26_lsm.c
dazuko-2.3.4/linux_conf.c
dazuko-2.3.4/linux_lsm_conf
dazuko-2.3.4/README.linux26
dazuko-2.3.4/patch_dpath.diff
dazuko-2.3.4/dazuko_dummyos.h
dazuko-2.3.4/dazuko_dummyos.c
dazuko-2.3.4/dazuko_events.h
dazuko-2.3.4/dazukoio_linux_compat1.h
dazuko-2.3.4/dazukoio_linux_compat1.c
dazuko-2.3.4/example_lua/
dazuko-2.3.4/example_lua/Makefile
dazuko-2.3.4/example_lua/README
dazuko-2.3.4/example_lua/config.lua
dazuko-2.3.4/example_lua/example.c
dazuko-2.3.4/example_lua/example.lua
dazuko-2.3.4/example_lua/libdazuko.c
dazuko-2.3.4/dazukoio_dummyos.c
dazuko-2.3.4/dazukoio_platform.h
dazuko-2.3.4/dazukoio_unix.h
dazuko-2.3.4/dazukoio_unix.c
dazuko-2.3.4/dazukoio_core.c
dazuko-2.3.4/example_ruby/
dazuko-2.3.4/example_ruby/Dazuko.c
dazuko-2.3.4/example_ruby/README
dazuko-2.3.4/example_ruby/example.rb
dazuko-2.3.4/example_ruby/extconf.rb
dazuko-2.3.4/example_ruby/test.rb
dazuko-2.3.4/dazuko_core.h
dazuko-2.3.4/dazuko_core.c
dazuko-2.3.4/README.trusted
dazuko-2.3.4/dazukoio_trusted.h
dazuko-2.3.4/dazuko_transport.c
dazuko-2.3.4/dazuko_version.h
dazuko-2.3.4/linux_dev_conf
dazuko-2.3.4/CHANGELOG
dazuko-2.3.4/patch_fsecure_init_event.diff
root@ania:/home/dazuko# tar xfvz dazuko-2.3.4.tar.gz 
dazuko-2.3.4/
dazuko-2.3.4/README
dazuko-2.3.4/LICENSE.GPL
dazuko-2.3.4/configure
dazuko-2.3.4/dazuko_freebsd.c
dazuko-2.3.4/dazuko_freebsd.h
dazuko-2.3.4/dazuko_linux.c
dazuko-2.3.4/dazuko_linux.h
dazuko-2.3.4/dazuko_platform.h
dazuko-2.3.4/dazukoio_trusted_core.c
dazuko-2.3.4/example_php/
dazuko-2.3.4/example_php/README
dazuko-2.3.4/dazukoio.h
dazuko-2.3.4/dazuko_transport.h
dazuko-2.3.4/dazukoio_dummyos.h
dazuko-2.3.4/dazukoio_core.h
dazuko-2.3.4/example_java/
dazuko-2.3.4/example_java/org/
dazuko-2.3.4/example_java/org/dazuko/
dazuko-2.3.4/example_java/org/dazuko/Dazuko.java
dazuko-2.3.4/example_java/org/dazuko/DazukoAccess.java
dazuko-2.3.4/example_java/README
dazuko-2.3.4/example_java/dazuko_jni.c
dazuko-2.3.4/example_java/org_dazuko_Dazuko.h
dazuko-2.3.4/example_java/Example.java
dazuko-2.3.4/example_c/
dazuko-2.3.4/example_c/example.c
dazuko-2.3.4/example_c/example_mt.c
dazuko-2.3.4/LICENSE.BSD
dazuko-2.3.4/COPYING
dazuko-2.3.4/dazuko_linux26.c
dazuko-2.3.4/dazuko_linux26.h
dazuko-2.3.4/dazuko_call.h
dazuko-2.3.4/dazuko_freebsd5.c
dazuko-2.3.4/dazuko_freebsd5.h
dazuko-2.3.4/dazuko_rsbac.c
dazuko-2.3.4/dazuko_rsbac.h
dazuko-2.3.4/example_perl/
dazuko-2.3.4/example_perl/t/
dazuko-2.3.4/example_perl/t/t01.t
dazuko-2.3.4/example_perl/t/t02.t
dazuko-2.3.4/example_perl/t/t03.t
dazuko-2.3.4/example_perl/t/t04.t
dazuko-2.3.4/example_perl/t/autounblock.inc
dazuko-2.3.4/example_perl/t/t05.t
dazuko-2.3.4/example_perl/Access.pm
dazuko-2.3.4/example_perl/Example.pl
dazuko-2.3.4/example_perl/ExampleOO.pl
dazuko-2.3.4/example_perl/IO.pm
dazuko-2.3.4/example_perl/IO.xs
dazuko-2.3.4/example_perl/Makefile.PL
dazuko-2.3.4/example_perl/Obj.pm
dazuko-2.3.4/example_perl/README
dazuko-2.3.4/example_perl/ExampleThr.pl
dazuko-2.3.4/example_python/
dazuko-2.3.4/example_python/MANIFEST
dazuko-2.3.4/example_python/README
dazuko-2.3.4/example_python/dazukomodule.c
dazuko-2.3.4/example_python/example.py
dazuko-2.3.4/example_python/setup.py
dazuko-2.3.4/dazuko_linux26_lsm.h
dazuko-2.3.4/dazuko_linux26_lsm.c
dazuko-2.3.4/linux_conf.c
dazuko-2.3.4/linux_lsm_conf
dazuko-2.3.4/README.linux26
dazuko-2.3.4/patch_dpath.diff
dazuko-2.3.4/dazuko_dummyos.h
dazuko-2.3.4/dazuko_dummyos.c
dazuko-2.3.4/dazuko_events.h
dazuko-2.3.4/dazukoio_linux_compat1.h
dazuko-2.3.4/dazukoio_linux_compat1.c
dazuko-2.3.4/example_lua/
dazuko-2.3.4/example_lua/Makefile
dazuko-2.3.4/example_lua/README
dazuko-2.3.4/example_lua/config.lua
dazuko-2.3.4/example_lua/example.c
dazuko-2.3.4/example_lua/example.lua
dazuko-2.3.4/example_lua/libdazuko.c
dazuko-2.3.4/dazukoio_dummyos.c
dazuko-2.3.4/dazukoio_platform.h
dazuko-2.3.4/dazukoio_unix.h
dazuko-2.3.4/dazukoio_unix.c
dazuko-2.3.4/dazukoio_core.c
dazuko-2.3.4/example_ruby/
dazuko-2.3.4/example_ruby/Dazuko.c
dazuko-2.3.4/example_ruby/README
dazuko-2.3.4/example_ruby/example.rb
dazuko-2.3.4/example_ruby/extconf.rb
dazuko-2.3.4/example_ruby/test.rb
dazuko-2.3.4/dazuko_core.h
dazuko-2.3.4/dazuko_core.c
dazuko-2.3.4/README.trusted
dazuko-2.3.4/dazukoio_trusted.h
dazuko-2.3.4/dazuko_transport.c
dazuko-2.3.4/dazuko_version.h
dazuko-2.3.4/linux_dev_conf
dazuko-2.3.4/CHANGELOG
dazuko-2.3.4/patch_fsecure_init_event.diff
root@ania:/home/dazuko# cd dazuko-2.3.4 
root@ania:/home/dazuko/dazuko-2.3.4# ./configure --mapfile=/boot/System.map-2.6.22-14-386 --disable-local-dpath --disable-chroot-support --enable-syscalls
checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... ok (cc)
kernel source in /lib/modules/2.6.22-14-386/source... no
kernel build source in /lib/modules/2.6.22-14-386/build... yes
kernel source in /lib/modules/2.6.22-14-386/build... yes
acquiring Linux kernel code configuration... ok
checking if Linux is RSBAC patched... no
checking if devfs is enabled... no
discovered host system... Linux (2.6.22)
checking for System.map file... ok (/boot/System.map-2.6.22-14-386)
locating sys_call_table... ok (0xc02e7540)
checking sys_call_table status... read-only

IMPORTANT NOTE:
If you get a kernel panic or segmentation fault while loading
the Dazuko module, you will need to reboot and try to
configure Dazuko again with the --sct-readonly option.

locating do_execve... ok (0xc016fb00)
identifying device API... ok
inspecting class type... ok (class)
inspecting suspend function... ok (suspend2)
inspecting task_struct structure... ok (using parent)
configure: creating Makefile
configure: creating library/Makefile
configure: creating example_c/Makefile

./configure successful

=======================
 Configuration summary
=======================

module events = ON_OPEN ON_CLOSE ON_EXEC
devfs support = no
rsbac support = no
hooking via syscalls = yes
local __d_path() = no (using chroot events, see README.linux26)
module debug = no
library 1.x compatibility = yes

root@ania:/home/dazuko/dazuko-2.3.4# make
make -C /lib/modules/2.6.22-14-386/build include/linux/version.h include/asm scripts
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.22-14-386'
  CHK     include/linux/version.h
make[1]: `include/asm' jest aktualne.
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.22-14-386'
make -C /lib/modules/2.6.22-14-386/build SUBDIRS="/home/dazuko/dazuko-2.3.4" modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.22-14-386'
  CC [M]  /home/dazuko/dazuko-2.3.4/dazuko_core.o
  CC [M]  /home/dazuko/dazuko-2.3.4/dazuko_transport.o
  CC [M]  /home/dazuko/dazuko-2.3.4/dazuko_linux.o
/home/dazuko/dazuko-2.3.4/dazuko_linux.c:90: error: conflicting types for ‘__d_path’
include/linux/dcache.h:303: error: previous declaration of ‘__d_path’ was here
make[2]: *** [/home/dazuko/dazuko-2.3.4/dazuko_linux.o] Error 1
make[1]: *** [_module_/home/dazuko/dazuko-2.3.4] Error 2
make[1]: leaving catalog `/usr/src/linux-headers-2.6.22-14-386'
make: *** [dummy_rule] Error 2
```

howto solve this problem ?

---

