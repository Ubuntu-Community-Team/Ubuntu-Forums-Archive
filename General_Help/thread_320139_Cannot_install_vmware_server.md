---
title: "Cannot install vmware server"
date: 2006-12-16
forum: General Help
---

### Post by celsofaf on 2006-12-16
I have downloaded latest VMware Server and ran the installation. Partial success. Then ran as root vmware-config.pl (as suggested after I typed 'vmware') to correct, but the _very same error_ occured. It is at the end of the output, take a look:

```
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
kernel? [/lib/modules/2.6.19/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.19/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config2/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config2/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-2.6.19'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove
it.  Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes]

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmnet-only'
make -C /lib/modules/2.6.19/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /tmp/vmware-config2/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config2/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config2/vmnet-only/userif.o
/tmp/vmware-config2/vmnet-only/userif.c: In function ‘VNetCopyDatagramToUser’:
/tmp/vmware-config2/vmnet-only/userif.c:629: error: ‘CHECKSUM_HW’ undeclared (first use in t                                               his function)
/tmp/vmware-config2/vmnet-only/userif.c:629: error: (Each undeclared identifier is reported                                                only once
/tmp/vmware-config2/vmnet-only/userif.c:629: error: for each function it appears in.)
make[2]: *** [/tmp/vmware-config2/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Yes, I visited the two sites it suggested, but it didn't help much.

I run Kubuntu 6.10 with the 2.6.19 kernel, if this helps! I had no problem whatsover installing vmware server two weeks ago, under Kubuntu 6.10 without "new kernel", before I formated my Kubuntu partition.

Thank you

---

### Post by chalex on 2006-12-16
You have to install the kernel sources and point the script to them.  Here's a port I wrote a while ago that may help: [http://yalb.net/wp/?p=60](http://yalb.net/wp/?p=60)

The package you want is linux-headers-`uname -r`

---

### Post by celsofaf on 2006-12-17
All right. I already had the linux.headers-2.6.19 package installed. I found the location of the headers at /usr/src/linux-headers-2.6.19/include and pointed this place to the script. It didn't work: same error. Seems like a problem with this "vmnet" module.

:/

---

### Post by yabbadabbadont on 2006-12-17
Try following this howto:

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server)

It has worked for many people, including me.  :)

---

### Post by celsofaf on 2006-12-17
Yes, that howto describes exactly what I did. :/

---

### Post by Spano on 2006-12-17
```
Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes]
```

How about answering "no" to this question, reset your networking and then see how the vmnet module compile goes?

Or maybe do a complete uninstall of VMware and try again.  Uninstall command is
```
vmware-uninstall.pl
```

---

### Post by riven0 on 2006-12-17
I had the same problem as you. VMware with kernel 2.6.19 just ***will not*** run. No joke. I had to revert back to 2.6.17 to get vmware working.

It sucks, especially since I spent all that time compiling the newest kernel, but oh well...:rolleyes:

---

### Post by celsofaf on 2006-12-17
OK OK... thank you all for the help! But now that I woke up, I did a Google search for 'vmware 2.6.19 kernel' (without the quotes) and I found the "any-any" script which would allow it to work with this kernel. It can be found here: [http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/) - and IT WORKED!!!!!!!!!!

:) :)

---

### Post by yabbadabbadont on 2006-12-17
> **celsofaf said:**
> OK OK... thank you all for the help! But now that I woke up, I did a Google search for 'vmware 2.6.19 kernel' (without the quotes) and I found the "any-any" script which would allow it to work with this kernel. It can be found here: [http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/) - and IT WORKED!!!!!!!!!!

:) :)

I completely missed the part where you identified your kernel.  Sorry.  When I was using Ubuntu, and installed vmware, I still had the older kernel.  In Gentoo, that "any-any" stuff is automatically applied by the ebuild that installs vmware server.  You might post a note about needing it on that howto thread I gave you the link to.  Hopefully the OP there will update his guide.

---

