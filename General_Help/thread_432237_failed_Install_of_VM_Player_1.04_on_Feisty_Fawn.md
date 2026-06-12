---
title: "failed Install of VM Player 1.04 on Feisty Fawn"
date: 2007-05-03
forum: General Help
---

### Post by eg-maverick on 2007-05-03
I tried to upgrade my VM player from 1.03 to 1.04 and got the following errors. I don't know what to do next. VM player 1.03 was working fine (but I was getting the memory leak). 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-15-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

Help!
Thanks,
Craig

---

### Post by eponymous on 2007-05-03
just got this precise error about 5 minutes ago, searching for help!

---

### Post by eponymous on 2007-05-03
trying this:
[http://icanthack.com/?p=53](http://icanthack.com/?p=53)

update: Worked!

```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successfully.

```

---

### Post by eg-maverick on 2007-05-04
Interesting. I tried this and I got the same error message. However, I did get a solution to work for me;


Petr's unofficial vmware-any-any-update109.tar.gz can be found here
[http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/) 

I installed and ran that patch and it fixed my problem. To do it:
1. download file
2. extract it
3. cd to the directory that contains runme.pl
4. Code: sudo ./runme.pl

Craig

---

