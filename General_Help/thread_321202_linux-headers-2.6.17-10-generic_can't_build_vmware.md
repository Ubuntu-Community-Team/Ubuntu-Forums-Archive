---
title: "linux-headers-2.6.17-10-generic can't build vmware server vmon module"
date: 2006-12-18
forum: General Help
---

### Post by hanzomon4 on 2006-12-18
I'm trying to build the vmon module for vmware sever but I can't because the linux-headers-2.6.17-10-generic is missing a file linux-headers-2.6.17-10-generic/arch/i386/Makefile. Here's the output:```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
Makefile:495: /usr/src/linux-headers-2.6.17-10-generic/arch/i386/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.17-10-generic/arch/i386/Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Any ideas?

---

### Post by koenn on 2006-12-18
/usr/src/linux-headers-2.6.17-10-generic/arch/i386/Makefile: No such file or directory

this file is missing;
it's usually provided by a headers dev package that you need to install before running the vmware install script. 
There are instructions for how to set up vmware server. did you read them ? did you install all required files ? the right way ? in the correct order ?

---

### Post by anaconda on 2006-12-18
This is because you have not installed kernel headers -packkage.
You can install them by:
```
sudo apt-get install linux-kernel-headers
```
or:
```
sudo apt-get install kernel-package
```

---

### Post by hanzomon4 on 2006-12-18
This is what I get with those two commands ```
 sudo apt-get install linux-kernel-headers
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-kernel-headers is a virtual package provided by:
  linux-libc-dev 2.6.17.1-10.34
You should explicitly select one to install.
E: Package linux-kernel-headers has no installation candidate

```

```
 sudo apt-get install kernel-package
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kernel-package is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.

```

And yes I have read the directions. Also I have setup vmware server before usually with a self compiled kernel. This is my first time trying it under the new generic kernel.  Also this **[COLOR="Red"]_is_[/COLOR]** on my system [LIST]
[*]`/usr/src/linux-headers-2.6.17-10-generic

This last part is not [LIST]
[*]/arch/i386/Makefile
[/LIST]
[/LIST]

---

### Post by hanzomon4 on 2006-12-18
This fixed it ```
 sudo aptitude reinstall linux-headers-2.6.17-10
``` I ls'ed the header dirs of the generic kernel and every thing was dead links pointing to   ../linux-headers-2.6.17-10

---

### Post by koenn on 2006-12-19
If I'm not mistaking, somewhere in the VMware installation instructions (or was it the ubuntu wiki ?) is a line saying you should 
```
apt-get install apt-get -y install linux-headers-'uname -r'
```
where uname -r would resolve to the kernel version of your system, and thus to
```
apt-get install apt-get install linux-headers-2.6.17-10 ...
``` or so on your computer. That, plus an list of other packages to install.

As the problem was obviously one of missing files (and directories), checking whether you'd installed all those required packages seemed like a reasonable thing to do, before looking at other probable causes. 

Glad you got it working

---

### Post by hanzomon4 on 2006-12-19
> **koenn said:**
> If I'm not mistaking, somewhere in the VMware installation instructions (or was it the ubuntu wiki ?) is a line saying you should 
```
apt-get install apt-get -y install linux-headers-'uname -r'
```
where uname -r would resolve to the kernel version of your system, and thus to
```
apt-get install apt-get install linux-headers-2.6.17-10 ...
``` or so on your computer. That, plus an list of other packages to install.

As the problem was obviously one of missing files (and directories), checking whether you'd installed all those required packages seemed like a reasonable thing to do, before looking at other probable causes. 

Glad you got it working

Well the package was installed already but some how the links were dead, I had to reinstall the package with aptitude to reconnect the links. Apt**_ install _**or aptitude**_ install_** just reported that the package was already installed.

---

### Post by koenn on 2006-12-20
I know, i've read your follow-up post.

---

