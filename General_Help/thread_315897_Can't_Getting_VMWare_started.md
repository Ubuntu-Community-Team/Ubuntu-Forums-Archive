---
title: "Can't Getting VMWare started"
date: 2006-12-09
forum: General Help
---

### Post by cephlon on 2006-12-09
Greetings, 
Trying to get VMware server running in Edgy. It seems to be installing ok, but when its done I can't open vmware. I get the same message. Below is my config process output. 

```
cephlon@feralandroid:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

cephlon@feralandroid:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
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
kernel? [/lib/modules/2.6.17-10-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport0, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport1, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport2, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/parport3, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet0, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet1, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet2, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet8, and was about to remove
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] n

Do you want networking for your virtual machines? (yes/no/help) [yes] y

This program previously created the file /dev/vmnet3, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet4, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet5, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet6, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet7, and was about to remove
it.  Somebody else apparently did it already.

This program previously created the file /dev/vmnet9, and was about to remove
it.  Somebody else apparently did it already.

Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [wizard] w

The following bridged networks have been defined:

. vmnet0 is bridged to eth0
. vmnet2 is bridged to ath0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] y

Configuring a NAT network for vmnet8.

The NAT network is currently configured to use the private subnet
172.16.180.0/255.255.255.0.  Do you want to keep these settings? [yes] y

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.180.0.

Do you wish to configure another NAT network? (yes/no) [no]

Do you want to be able to use host-only networking in your virtual machines?
[yes]

Configuring a host-only network for vmnet1.

The host-only network is currently configured to use the private subnet
192.168.146.0/255.255.255.0.  Do you want to keep these settings? [yes]

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 192.168.146.0.

Do you wish to configure another host-only network? (yes/no) [no]

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Please specify a port for remote console connections to use [902]

Stopping internet superserver: xinetd.
Starting internet superserver: xinetd.
Configuring the VMware VmPerl Scripting API.

Building the VMware VmPerl Scripting API.

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Installing the VMware VmPerl Scripting API.

The installation of the VMware VmPerl Scripting API succeeded.

Generating SSL Server Certificate

In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines] /home/cephlon/vmMachine

The path "/home/cephlon/vmMachine" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

Do you want to enter a serial number now? (yes/no/help) [no] y

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  98W6T-Y21AD-2FQ27-4222W

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Bridged networking on /dev/vmnet2                                  failed
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.1 build-29996 for Linux for this running
kernel completed successfully.


cephlon@feralandroid:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

                                                                                            

```

---

### Post by cephlon on 2006-12-10
Well after a couple hours of searching I found the solution. I hope it helps someone else:
[URL="http://www.karakas-online.de/forum/viewtopic.php?t=909"]
http://www.karakas-online.de/forum/viewtopic.php?t=909[/URL]

---

