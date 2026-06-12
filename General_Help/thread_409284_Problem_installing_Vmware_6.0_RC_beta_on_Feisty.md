---
title: "Problem installing Vmware 6.0 RC beta on Feisty"
date: 2007-04-14
forum: General Help
---

### Post by hdotcom on 2007-04-14
Hi,

I am a linux newbie and thought i'd start off learning linux by using ubuntu. I installed ver 6.10 on my ThinkPad T60 (without updating it) and faced several problems with the display and the overall performance despited following the online guides for T60. 

I then decided to install Feisty and that worked great. The only problem is i wasnt able to install Vmware 6.0 RC beta. The installation completed with no errors but for some odd reason once Ubuntu was restarted and i doubled clicked on the icon it wont load! It would just open a window that says starting vmware workstation and then disappear.

Any idea what went wrong? 

Cheers!

---

### Post by hdotcom on 2007-04-14
Just an update...i couldnt even get Vmware 5.5 to work. It had the same problem and and when I ran /usr/bin/vmware this is the message that i got:

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

And when i ran vmware-config.pl i got numerous errors! Even though i applied the any-to-any patch and followed the config steps. Have a look at the output.

Building the vmmon module.

Building for VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV3]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX1]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV2]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1522: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1523: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2073: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:1713: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

Any idea?

Rgds,

H.

---

