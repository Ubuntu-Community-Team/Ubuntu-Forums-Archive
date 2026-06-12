---
title: "How to install VMWare on Ubuntu Desktop 7.0.4"
date: 2007-08-13
forum: General Help
---

### Post by LinuxTek on 2007-08-13
I downloaded and tried to install VMWare server but get this error message:
(any ideas on how to fix this?)

I tried to log a support ticket on VMWare's site but their forums are broken (login and get sent to registration page, hit continue and get sent back to the registration page).

thanks

vmtek

---
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by jonathanmc on 2007-08-13
I haven't tried it yet, but was hoping to in the next week or so 

but this may help
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by upthelum on 2007-08-13
Have a look through my previous posts as i managed to get it installed. You could try Synaptic and you may need the header files. Check this [_site_]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto?") for starters.

---

### Post by fjgaude on 2007-08-14
All I did in Feisty was use Synaptic and installed vmware server. The rest is history. Install was fast and easy, then install WinXP and then Xara (my main reason for needing Windows). Wow, easy... and it is fast. I set 10Gs for disk space and 512Ms for RAM. After installing the VM Tools, things got fast, quick, just about as fast as my box under Linux. So I'm a happy camper.

frank

---

