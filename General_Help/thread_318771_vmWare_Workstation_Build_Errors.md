---
title: "vmWare Workstation Build Errors"
date: 2006-12-14
forum: General Help
---

### Post by gavinjb on 2006-12-14
Hi,

I am trying to install VmWare Workstation on Edgy, but it gets to the stage of building the vmmon module and then it fails (see below), has anyone got any ideas

```

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:44:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_defs.h:208:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./include/vcpuset.h:56,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:45:
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:54:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:19,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:45:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:19,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:45:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:62: error: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_asm.h:23,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:48:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/linux/driver.c:138: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:142: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I have searched through this forum and done a google searches, but cant seem to find an answer for this, can any one help.

Thanks,


Gavin,

---

### Post by sefs on 2006-12-14
I see in the bottom is  using the heards "/usr/src/linux-headers-2.6.17-10-generic"

Is that normal? or do you have to down load the headers for your specific distribution, something that looks like "/usr/src/linux-headers-2.6.17-10-386" and "/usr/src/linux-headers-2.6.17-10"

You can look at that until someone else comes along that can shed some light on that.

---

### Post by gavinjb on 2006-12-14
I did have to download some headers the other day, to install TrueCrypt on my System, but I was getting this error before I even tried to install TrueCrypt.

Gavin,

---

### Post by anchor on 2006-12-15
I had the exact same issue.

I downloaded this script:

```

#!/bin/bash

START=`pwd`

tar zxvf $START/VMware-workstation-5.5.1-19175.tar.gz
cd $START/vmware-distrib/lib/modules/source/

for foo in vmmon vmnet; do 
	tar xf $foo.tar
	perl -pi -e 's,-Werror,-DKBUILD_BASENAME=\\"\$\(DRIVER\)\\" \\\n\t-Werror,g' ${foo}-only/Makefile.kernel
	mv ${foo}.tar ${foo}.tar.vm
	tar cf ${foo}.tar ${foo}-only
done

cd $START/vmware-distrib

ls -lart

```


It fixed everything right up.  Note: I did not write this script, I found it after a lengthy google search:

Here's the google cache of the original page.
[http://72.14.253.104/search?q=cache:tDQgwr_oyMQJ:blog.gnu-designs.com/2006/08/07/fix-vmware-vmw_have_epoll-error-message-with-current-distributions/+vmmon+vmware+VMW_HAVE_EPOLL&hl=en&gl=us&ct=clnk&cd=1](http://72.14.253.104/search?q=cache:tDQgwr_oyMQJ:blog.gnu-designs.com/2006/08/07/fix-vmware-vmw_have_epoll-error-message-with-current-distributions/+vmmon+vmware+VMW_HAVE_EPOLL&hl=en&gl=us&ct=clnk&cd=1)

---

### Post by luckymonkey on 2006-12-16
After runing the script the configuration of vmware finished ok, but i could not run the app...

jose@jose-desktop:~$ /usr/bin/vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
GTK Accessibility Module initialized
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/libspi.so.0: undefined symbol: atk_hyperlink_impl_get_type

Can anyone help me please!!!?

---

### Post by gavinjb on 2006-12-17
Thanks for the script, didn't work though, it still fails at the same place, only thing now is that I notice that the install script stops a lot more vmware services.

```

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmnet-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config2/vmnet-only/driver.o
In file included from /tmp/vmware-config2/vmnet-only/vnet.h:14,
                 from /tmp/vmware-config2/vmnet-only/vnetInt.h:10,
                 from /tmp/vmware-config2/vmnet-only/driver.c:40:
/tmp/vmware-config2/vmnet-only/vm_atomic.h:54:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmnet-only/vm_oui.h:13,
                 from /tmp/vmware-config2/vmnet-only/vnetInt.h:11,
                 from /tmp/vmware-config2/vmnet-only/driver.c:40:
/tmp/vmware-config2/vmnet-only/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmnet-only/driver.c: In function ‘VNetProcessOwnsPort’:
/tmp/vmware-config2/vmnet-only/driver.c:1698: error: ‘struct files_struct’ has no member named ‘max_fds’
make[2]: *** [/tmp/vmware-config2/vmnet-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


```

---

### Post by ture_atlantis on 2006-12-19
i got this same error, but i was using the 64bit version of ubuntu, i had to do a

sudo apt-get install ia32-libs

and it worked fine after that.  i got that clue from this web page.... 

[http://users.piuha.net/martti/comp/ubuntu/server.html#6](http://users.piuha.net/martti/comp/ubuntu/server.html#6)


hope that helps

---

### Post by Eigenwert on 2007-01-20
Has anyone found a fix for this? The script didn't help me at all. I'm still getting the following error message after implimenting all of the changes from the script:

```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.17-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/./include/vmware.h:24,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:44:
/tmp/vmware-config4/vmmon-only/./include/vm_basic_defs.h:208:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config4/vmmon-only/./include/vcpuset.h:56,
                 from /tmp/vmware-config4/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config4/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:45:
/tmp/vmware-config4/vmmon-only/./include/vm_atomic.h:54:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.h:19,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:45:
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.h:19,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:45:
/tmp/vmware-config4/vmmon-only/./include/compat_wait.h:60: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:62: error: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-config4/vmmon-only/./include/vm_asm.h:23,
                 from /tmp/vmware-config4/vmmon-only/linux/driver.c:48:
/tmp/vmware-config4/vmmon-only/./include/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined
/tmp/vmware-config4/vmmon-only/linux/driver.c:138: warning: initialization from incompatible pointer type
/tmp/vmware-config4/vmmon-only/linux/driver.c:142: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

```

Thanks

EW

---

### Post by gavinjb on 2007-01-20
Hi,

Like wise I have had no luck, I have given up and am beginning to look at OpenSource alternatives as I only had the trial version.

Gavin,

---

### Post by Starseed on 2007-12-18
I got it to work by using the any-any patch:

[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz)


It successfully installed workstation 5.5 on ubuntu 7.10 running on a Dell Latitude D620.

---

### Post by gavinjb on 2007-12-18
Hi,

in the end I installed VirtualBox and am using it in seemless mode with no problems (Even seems to run faster than vm)

---

### Post by danwood76 on 2007-12-18
yes the any-any patch is necessary to compile VMware workstation modules.

Confirmed and working on feisty and gutsy with Vmware Workstation 5.5

---

