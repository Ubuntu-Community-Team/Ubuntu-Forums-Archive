---
title: "Error installing vmware workstation 6"
date: 2008-06-07
forum: General Help
---

### Post by Fredrik_b on 2008-06-07
Hi when I am trying to install vmware worksation I get this error.

```
None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config0/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config0/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config0/vmmon-only/common/vmx86.h:18,
                 from /tmp/vmware-config0/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config0/vmmon-only/common/cpuid.c:14:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I have installed build essentials and xinetd according to some instructions i found.

What have I missed?

I use "Kubuntu 8.04 USB Persistent install" running from a USB pendrive ([www.pendrivelinux.com](www.pendrivelinux.com))

// Fredrik

---

### Post by balki2005 on 2008-06-08
hello, 

here is the answer:  ( I found  it on [http://eitchpress.eitchnet.ch/?p=13](http://eitchpress.eitchnet.ch/?p=13)) 

VMWare 6 and Ubuntu Hardy: vmmon compile error

Just a quick post to documentate how I got my VMWare config to work:

Problem: include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly, and vmmon-only compile failes

Solution: change line 74 in vmmon-only source file to read: #include &#8220;linux/bitops.h&#8221;

Steps:

   1. cd /usr/lib/vmware/modules/source
   2. cp vmmon.tar vmmon.tar.orig
   3. sudo tar xvf vmmon.tar
   4. cd vmmon-only/include/
   5. sudo vi vcpuset.h
   6. change line 74 from: #include &#8220;asm/bitops.h&#8221; to: #include &#8220;linux/bitops.h&#8221;
   7. rm vmmon.tar
   8. sudo tar cvf vmmon.tar vmmon-only/
   9. sudo rm -rf vmmon-only/
  10. sudo vmware-config.pl

That&#8217;s it, the compile will work now and vmware should be usable as normal.

Kind regards,

Balki2005

---

