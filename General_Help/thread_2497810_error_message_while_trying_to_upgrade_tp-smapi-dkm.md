---
title: "error message while trying to upgrade: tp-smapi-dkms E: Sub-process /usr/bin/dpkg ret"
date: 2024-05-18
forum: General Help
---

### Post by celak on 2024-05-18
I've been using Ubuntu for a few years but I'm a fairly basic user.
 
apologies for long post, not sure if all is relevant

I am receiving this error message when trying to sudo apt upgrade:

```
sudo apt upgrade -y
[sudo] password for do: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  python3-update-manager update-manager update-manager-core
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up tp-smapi-dkms (0.43-1ubuntu1) ...
Removing old tp_smapi-0.43 DKMS files...
Deleting module tp_smapi-0.43 completely from the DKMS tree.
Loading new tp_smapi-0.43 DKMS files...
Building for 6.5.0-35-generic
Building initial module for 6.5.0-35-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/tp-smapi-dkms.0.crash'
Error! Bad return status for module build on kernel: 6.5.0-35-generic (x86_64)
Consult /var/lib/dkms/tp_smapi/0.43/build/make.log for more information.
dpkg: error processing package tp-smapi-dkms (--configure):
 installed tp-smapi-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 tp-smapi-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

what does this mean and can I fix it?

I've tried googling but cannot understand the answers that I found. 

I tried the solutions detailed here but they did not work: [https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/](https://www.tecmint.com/sub-process-usr-bin-dpkg-returned-an-error-in-ubuntu/)
I don't know what the package is that is causing the problem referred to in the last solution there. 

I also asked chatgpt and it said i could find more info by using

```
sudo cat /var/lib/dkms/tp_smapi/0.43/build/make.log
```
I know what cat does so I wasn't worried about using it, although I know gpt can't be relied on. 


the output is
```
sudo cat /var/lib/dkms/tp_smapi/0.43/build/make.log
DKMS make.log for tp_smapi-0.43 for kernel 6.5.0-35-generic (x86_64)
Sat 18 May 18:36:26 BST 2024
make: Entering directory '/usr/src/linux-headers-6.5.0-35-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
  You are using:           gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0
  CC [M]  /var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.o
  CC [M]  /var/lib/dkms/tp_smapi/0.43/build/tp_smapi.o
  CC [M]  /var/lib/dkms/tp_smapi/0.43/build/hdaps.o
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:94:42: error: macro "DEFINE_SEMAPHORE" requires 2 arguments, but only 1 given
   94 | static DEFINE_SEMAPHORE(thinkpad_ec_mutex);
      |                                          ^
In file included from /var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:45:
./include/linux/semaphore.h:34: note: macro "DEFINE_SEMAPHORE" defined here
   34 | #define DEFINE_SEMAPHORE(_name, _n)     \
      | 
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:94:8: error: type defaults to ‘int’ in declaration of ‘DEFINE_SEMAPHORE’ [-Werror=implicit-int]
   94 | static DEFINE_SEMAPHORE(thinkpad_ec_mutex);
      |        ^~~~~~~~~~~~~~~~
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c:115:36: error: macro "DEFINE_SEMAPHORE" requires 2 arguments, but only 1 given
  115 | static DEFINE_SEMAPHORE(smapi_mutex);
      |                                    ^
In file included from ./include/linux/fs.h:25,
                 from ./include/linux/proc_fs.h:10,
                 from /var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c:41:
./include/linux/semaphore.h:34: note: macro "DEFINE_SEMAPHORE" defined here
   34 | #define DEFINE_SEMAPHORE(_name, _n)     \
      | 
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c:115:8: error: type defaults to ‘int’ in declaration of ‘DEFINE_SEMAPHORE’ [-Werror=implicit-int]
  115 | static DEFINE_SEMAPHORE(smapi_mutex);
      |        ^~~~~~~~~~~~~~~~
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c: In function ‘thinkpad_ec_lock’:
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:112:35: error: ‘thinkpad_ec_mutex’ undeclared (first use in this function); did you mean ‘thinkpad_ec_lock’?
  112 |         ret = down_interruptible(&thinkpad_ec_mutex);
      |                                   ^~~~~~~~~~~~~~~~~
      |                                   thinkpad_ec_lock
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:112:35: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c: In function ‘store_battery_start_charge_thresh’:
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c:780:15: error: ‘smapi_mutex’ undeclared (first use in this function)
  780 |         down(&smapi_mutex);
      |               ^~~~~~~~~~~
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c:780:15: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c: In function ‘thinkpad_ec_try_lock’:
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:126:30: error: ‘thinkpad_ec_mutex’ undeclared (first use in this function); did you mean ‘thinkpad_ec_lock’?
  126 |         return down_trylock(&thinkpad_ec_mutex);
      |                              ^~~~~~~~~~~~~~~~~
      |                              thinkpad_ec_lock
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c: In function ‘store_battery_stop_charge_thresh’:
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c:822:15: error: ‘smapi_mutex’ undeclared (first use in this function)
  822 |         down(&smapi_mutex);
      |               ^~~~~~~~~~~
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c: In function ‘thinkpad_ec_unlock’:
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:138:13: error: ‘thinkpad_ec_mutex’ undeclared (first use in this function); did you mean ‘thinkpad_ec_lock’?
  138 |         up(&thinkpad_ec_mutex);
      |             ^~~~~~~~~~~~~~~~~
      |             thinkpad_ec_lock
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c: In function ‘thinkpad_ec_try_lock’:
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:127:1: error: control reaches end of non-void function [-Werror=return-type]
  127 | }
      | ^
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c: At top level:
/var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.c:94:8: warning: ‘DEFINE_SEMAPHORE’ defined but not used [-Wunused-variable]
   94 | static DEFINE_SEMAPHORE(thinkpad_ec_mutex);
      |        ^~~~~~~~~~~~~~~~
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c: At top level:
/var/lib/dkms/tp_smapi/0.43/build/tp_smapi.c:115:8: warning: ‘DEFINE_SEMAPHORE’ defined but not used [-Wunused-variable]
  115 | static DEFINE_SEMAPHORE(smapi_mutex);
      |        ^~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:251: /var/lib/dkms/tp_smapi/0.43/build/thinkpad_ec.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [scripts/Makefile.build:251: /var/lib/dkms/tp_smapi/0.43/build/tp_smapi.o] Error 1
make[1]: *** [/usr/src/linux-headers-6.5.0-35-generic/Makefile:2039: /var/lib/dkms/tp_smapi/0.43/build] Error 2
make: *** [Makefile:234: __sub-make] Error 2
make: Leaving directory '/usr/src/linux-headers-6.5.0-35-generic'
```


I'm not sure if it is unrelated but I've also been having issues with overheating, and in addition, the battery charging threshold is not working properly. I can give more info on this if it is relevant


Thanks

Edit - I just reinstalled in the end, see if it comes up again.

---

### Post by currentshaft on 2024-05-20
?

---

