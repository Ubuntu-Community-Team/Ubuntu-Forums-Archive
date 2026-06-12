---
title: "VMWare Server Build Errors"
date: 2007-06-03
forum: General Help
---

### Post by Beamerboy on 2007-06-03
Hey,

I just upgraded my kernel and tried to run vmware-config.pl in order to rebuild vmware for the new kernel but I get the following error:

```

vmware-config.pl 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-5-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.22-5-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-5-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config6/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
include/asm/page.h: In function ‘pte_t native_make_pte(long unsigned int)’:
include/asm/page.h:112: error: expected primary-expression before ‘)’ token
include/asm/page.h:112: error: expected ‘;’ before ‘{’ token
include/asm/page.h:112: error: expected primary-expression before ‘.’ token
include/asm/page.h:112: error: expected `;' before ‘}’ token
make[2]: *** [/tmp/vmware-config6/vmmon-only/common/task.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-5-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I have had this problem before but I can't remember how I fixed it :/

Any help appreciated

Paladine

---

### Post by Beamerboy on 2007-06-03
Bump

---

### Post by veloce on 2007-06-04
you can either 

[LIST=1]
[*]patch the vmware-config with what's affectionately know as the "any-any" patch.
[*]uninstall vmware server and reinstall from the commercial repository.
[/LIST]

Instructions for these are on two or three threads.

---

### Post by Beamerboy on 2007-06-04
Problem with the commercial repo is networking was I had issues with networking, I could get out of the guest fine, but I couldn't connect to it.  This problem disappeared as soon as I install from the official vmware binary.

I tried the any any patch and it made no difference :/

Paladine

---

### Post by veloce on 2007-06-05
> **Beamerboy said:**
> Problem with the commercial repo is networking was I had issues with networking, I could get out of the guest fine, but I couldn't connect to it.  This problem disappeared as soon as I install from the official vmware binary.

I tried the any any patch and it made no difference :/

Paladine

The difference is in the set of virtual networks set up by default.  

The repo version sets up one of each network type.  Routing can get confusing in this situation - there are two possible routes btw the vm and host and vm or host have to match.

You can easily change the virtual network settings with:

vmware-config-network.pl

(Now if you want to disable dhcp on the nat or host only network - that is another thing entirely!)

---

