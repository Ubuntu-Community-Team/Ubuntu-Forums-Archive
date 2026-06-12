---
title: "VMWare install problem in 7.04"
date: 2007-04-21
forum: General Help
---

### Post by sg3524 on 2007-04-21
I recently upgraded a 6.10 install to 7.04.  Probably should have thought about this before proceeding....

My VMWare would not run after upgrade.  I know VMWare needs to be reconfigured whenever you change Kernels, so proceeded to run vmware-config.pl configuration utility.

I got the following error, after which I downloaded the latest version of VMWare to see if it would resolve (reinstalled over previous ver), which it did not.  This looks like a problem with the format of the clib included files (I am not a C prgrammer, so hoping someone can confirm or suggest workaround).  The output of the script was :

> Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config6/vmmon-only/linux/driver.c:80:
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config6/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.


Since 7.04 is not officially supported by VMWare any suggestions, guesses, or recommendations are welcome.  

I have reinstalled libc-dev too, and checked to be sure that all directories exist.

---

### Post by rbmorse on 2007-04-21
First of all, which VMware package are you trying to use?

The Workstation 6 (RC) is currently in testing and available for no charge from VMWare. It works great with Fiesity. Recommended. 

VMServer and VMplayer will just have to wait until the new packages are built and placed in repository...I suspect VMware won't update the tarballs untill after Workstation 6 is released so they can incorporate some of the improvements.

---

### Post by sg3524 on 2007-04-21
Was trying to install VMWare server.

Installed Workstation RC6 and all is good again \\:D/ .  Just had to find my old vmx files :)

Thanks!!!

---

### Post by krimson on 2007-04-22
when i get the newest vmware workstation beta 6 (VMware-workstation-6.0.0-44426.i386.rpm) in rpm, i used alien to convert it, then i used right-click GDebi to install it, then i run it, and it says "Starting VMware Worstation" in the bottom, and then just goes away.

when i converted, i didnt use any special switches or anything... did i do something wrong?

---

### Post by nandasunu on 2007-04-24
> **krimson said:**
> when i get the newest vmware workstation beta 6 (VMware-workstation-6.0.0-44426.i386.rpm) in rpm, i used alien to convert it, then i used right-click GDebi to install it, then i run it, and it says "Starting VMware Worstation" in the bottom, and then just goes away.

when i converted, i didnt use any special switches or anything... did i do something wrong?

In my experience it is always best to install vmware from the tar.gz instead of the .rpm, even on a .rpm based distro. I have always had problems with the .rpm and the tar.gz is pretty easy to set up, I would try that instead.

---

### Post by rbmorse on 2007-04-24
What he says.  Installing VMWare from the tarball is about as easy as it gets. The setup is long and asks you lots of questions, but the defaults are sane and whatever finger you use to  press the <enter> key gets good exercise. 

hint: When you get to the part where you have to read the user agreement, the <spacebar> will advance the text.

---

### Post by wrycatcher on 2007-04-24
Try this:

[http://ubuntuforums.org/showthread.php?t=421904](http://ubuntuforums.org/showthread.php?t=421904)

---

