---
title: "VMWare Server problems"
date: 2008-01-03
forum: General Help
---

### Post by -Zeus- on 2008-01-03
I install vmware server 1.0.4 from the VMWare website since it is *sigh* still not in the repos.  It installs OK but when I run vmware-config.pl I get this output at the bottom.

```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed

The configuration of VMware Server 1.0.4 build-56528 for Linux for this running
kernel completed successfully.
```

When I try to run VMWare I get this error:
```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```


I have seen no other errors throughout the install.
Any ideas?

---

### Post by zvacet on 2008-01-03
Why did you run that command?Look [here](http://www.howtoforge.com/vmware_server_1.0.4_plus_mui_ubuntu_7.04) how  install proces goes.Anyway run in terminal


```
/usr/bin/vmware-config.pl.
```

---

### Post by -Zeus- on 2008-01-03
that command is what i've been running... I already installed it but it said I have to run this because of that 2nd error I posted...

---

### Post by -Zeus- on 2008-01-03
*bump* anyone?

---

### Post by Kzin on 2008-01-03
When you run the vmware config script, can u paste what you have listed under the vmnets?

---

### Post by sciencewhiz on 2008-01-03
did you run the command with sudo?

---

### Post by -Zeus- on 2008-01-03
what do you mean "under the vmnets"?

Here's the whole output.
```
/:$ sudo vmware-config.pl 
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
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
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [no] 

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Would you prefer to modify your existing networking configuration using the 
wizard or the editor? (wizard/editor/help) [wizard]  

The following bridged networks have been defined:

. vmnet0 is bridged to ath0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] n

Removing a NAT network for vmnet8.

Do you want to be able to use host-only networking in your virtual machines? 
[no] n

Removing a host-only network for vmnet1.

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config1/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /tmp/vmware-config1/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config1/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
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

The file /etc/rc2.d/K08vmware that this program was about to install already 
exists.  Overwrite? [yes] 

In which directory do you want to keep your virtual machine files? 
[/root/.vmware] 

Do you want to enter a serial number now? (yes/no/help) [no] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed

The configuration of VMware Server 1.0.4 build-56528 for Linux for this running
kernel completed successfully.

/:$ 
```

Here's what I get when trying to launch VMWare

```
/:$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

/:$ 
```

---

### Post by vahnx on 2008-01-03
I know this might not be the best solution and I don't know if it will work, but I was having so many problems following guides to install VMWare Server, then I decided to do everything myself. I completely removed all traces of VMWare, then ran sudo vmware-config.pl and when all the prompts were appearing, I just kept hitting enter then it finally installed and worked. So instead of typing in [no], etc., just press enter.

---

### Post by -Zeus- on 2008-01-03
I've already tried that... that's what I first did

---

### Post by Kzin on 2008-01-03
I also had some troubles setting up the network.  In the config, remove the bridged network.  Run the config again and re add it.  This should work.

---

### Post by dcstar on 2008-01-03
> **-Zeus- said:**
> I install vmware server 1.0.4 from the VMWare website since it is *sigh* still not in the repos. 
........

It** IS** in the repos, simply enable the Third party "Partner" option in Synaptic.

---

