---
title: "various make errors"
date: 2008-07-01
forum: General Help
---

### Post by vaineh on 2008-07-01
hi

trying to install some drivers on ubuntu hardy and im falling at the second hurdle. or maybe the first and i just dont know it. ./configure seems to go ok, but make is spitting out lots of errors. can anyone shed some light on what they mean 

> $ make
make  all-recursive
make[1]: Entering directory `/home/test/visdn-0.14.0'
Making all in etc
make[2]: Entering directory `/home/test/visdn-0.14.0/etc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/test/visdn-0.14.0/etc'
Making all in scripts
make[2]: Entering directory `/home/test/visdn-0.14.0/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/test/visdn-0.14.0/scripts'
Making all in visdn-core
make[2]: Entering directory `/home/test/visdn-0.14.0/visdn-core'
make -C /lib/modules/2.6.22-14-generic/build modules M=/home/test/visdn-0.14.0/visdn-core
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/test/visdn-0.14.0/visdn-core/core_main.o
In file included from /home/test/visdn-0.14.0/visdn-core/core_main.c:26:
/home/test/visdn-0.14.0/visdn-core/cxc.h:38: error: field ‘subsys’ has incomplete type
/home/test/visdn-0.14.0/visdn-core/cxc.h: In function ‘visdn_cxc_get’:
/home/test/visdn-0.14.0/visdn-core/cxc.h:85: warning: type defaults to ‘int’ in declaration of ‘__mptr’
/home/test/visdn-0.14.0/visdn-core/cxc.h:85: warning: initialization from incompatible pointer type
/home/test/visdn-0.14.0/visdn-core/core_main.c: At top level:
/home/test/visdn-0.14.0/visdn-core/core_main.c:55: error: unknown field ‘hotplug’ specified in initializer
/home/test/visdn-0.14.0/visdn-core/core_main.c:55: warning: initialization from incompatible pointer type
make[4]: *** [/home/test/visdn-0.14.0/visdn-core/core_main.o] Error 1
make[3]: *** [_module_/home/test/visdn-0.14.0/visdn-core] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/test/visdn-0.14.0/visdn-core'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/test/visdn-0.14.0'
make: *** [all] Error 2

cheers

---

