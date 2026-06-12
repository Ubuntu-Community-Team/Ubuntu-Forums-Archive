---
title: "VMware Install Problems"
date: 2006-08-02
forum: General Help
---

### Post by WhistlerUK on 2006-08-02
> 
Do you wish to configure another NAT network? (yes/no) [no]

Do you want to be able to use host-only networking in your virtual machines?
[yes]

Configuring a host-only network for vmnet1.

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.15.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.15.0.

Do you wish to configure another host-only network? (yes/no) [no]

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmnet-only'
make -C /lib/modules/2.6.15-26-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /tmp/vmware-config4/vmnet-only/driver.o
In file included from /tmp/vmware-config4/vmnet-only/vnet.h:14,
                 from /tmp/vmware-config4/vmnet-only/vnetInt.h:10,
                 from /tmp/vmware-config4/vmnet-only/driver.c:40:
/tmp/vmware-config4/vmnet-only/vm_atomic.h:54:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config4/vmnet-only/vm_oui.h:13,
                 from /tmp/vmware-config4/vmnet-only/vnetInt.h:11,
                 from /tmp/vmware-config4/vmnet-only/driver.c:40:
/tmp/vmware-config4/vmnet-only/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmnet-only/driver.c: In function ‘VNetProcessOwnsPort’:
/tmp/vmware-config4/vmnet-only/driver.c:1698: error: ‘struct files_struct’ has no member named ‘max_fds’
make[2]: *** [/tmp/vmware-config4/vmnet-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.



Any Ideas what the problem might be?

---

