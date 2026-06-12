---
title: "Vmware after Edgy upgrade"
date: 2007-01-16
forum: General Help
---

### Post by dixxxxer on 2007-01-16
Some serious problem with vmware.
I upgraded Drake to Edgy then tried to reconfigure vmware but no results.
Ok, I've installed kernel headers etc. 
Here's the error after sudo /usr/bin/vmware-config.pl:

> Building the vmmon module.

Using 2.6.x kernel build system.
make: Siirrytään hakemistoon "/tmp/vmware-config2/vmmon-only"
make -C /usr/src/linux-headers-2.6.17-10-386/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Siirrytään hakemistoon "/usr/src/linux-headers-2.6.17-10-386"
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:62: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config2/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Virhe 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Virhe 2
make[1]: Poistutaan hakemistosta "/usr/src/linux-headers-2.6.17-10-386"
make: *** [vmmon.ko] Virhe 2
make: Poistutaan hakemistosta "/tmp/vmware-config2/vmmon-only"
Unable to build the vmmon module.


Any ideas what's the deal? :(

---

### Post by dixxxxer on 2007-01-16
Ok, I got it fixed :)
Here's the instructions.

Grab the latest vmware-any-any-updateNN.tar.gz file from
[http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/) untar and execute runme.pl

---

