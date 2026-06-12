---
title: "Error Cant install or update"
date: 2008-01-28
forum: General Help
---

### Post by supertails on 2008-01-28
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I fix it?

---

### Post by SOULRiDER on 2008-01-28
Open a terminala dn type
```
sudo dpkg --configure -a
```
and paste the output.

---

### Post by supertails on 2008-01-28
Setting up linux-headers-2.6.24 (86) ...

That's it.

---

### Post by SOULRiDER on 2008-01-28
its probably installing that package.. does it stay there?

---

### Post by supertails on 2008-01-28
No. Nothing at all just that.

---

### Post by SOULRiDER on 2008-01-29
I'm gonna tag this thread so others from the unanswered posts team can help.

---

### Post by danwood76 on 2008-01-29
can you install and update now that you have run the dpkg reconfigure?

regards,
Danny

---

### Post by plucky on 2008-01-29
> Setting up linux-headers-2.6.24 (86) ...

Are you running Hardy Heron kernel?

Can you post the outputs of the following commands ```
cat /etc/apt/sources.list
uname -a
```

---

### Post by supertails on 2008-01-29
tails@tails-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
tails@tails-laptop:~$ uname -a
Linux tails-laptop 2.6.24 #1 SMP Tue Jan 29 15:56:53 EST 2008 i686 GNU/Linux
tails@tails-laptop:~$

---

### Post by supertails on 2008-01-30
tails@tails-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
tails@tails-laptop:~$ 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by plucky on 2008-01-30
> dpkg: requested operation requires superuser privilege You need to use **sudo** in front of that command.

> Linux tails-laptop **2.6.24** #1 SMP Tue Jan 29 15:56:53 EST 2008 i686 GNU/Linux

I don't know why you have that kernel , this is my output for the **uname -a** command > Linux ubuntu-test 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

Yet your sources.list looks ok. I don't understand

---

### Post by danwood76 on 2008-01-30
I think one of your problems is you are using the latest stable linux kernel.
And for a more experianced linux user this is fine for someone new to linux you should really start with the standard one that comes with ubuntu, otherwise all of the software packages that are in the repos may not function correctly.

regards,
Danny

---

### Post by supertails on 2008-01-30
tails@tails-laptop:~$ sudo dpkg --configure -a
[sudo] password for tails:
Setting up linux-headers-2.6.24 (86) ...

tails@tails-laptop:~$ 


I got kernel 2.6.24 because I wanted to recompile the kernel and I don't know why kernel 2.6.22-14 was on there at first but I guess I needed to restart my computer before the new kernel was install completely.

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package linux-image-2.6.24 needs to be reinstalled, but I can't find an archive for it.'

---

### Post by danwood76 on 2008-01-30
When you re-compile the kernel, if done correctly, the header files are generated automatically. You wont be able to install them through synaptic (I dont think) as they wont be in gutsy repos.
That will be why you are getting that error
> 'E:The package linux-image-2.6.24 needs to be reinstalled, but I can't find an archive for it.'

I would try recompiling the kernel, making sure you do it the ubuntu way which auto generates the header files.
Im running 2.6.24 at home and never had any of the issues you have had.

regards,
Danny

---

### Post by supertails on 2008-01-30
How do I recompile the ubuntu way?

---

### Post by danwood76 on 2008-01-30
the link that was given to you in the other thread should do it fine.
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

the line that says
```
fakeroot make-kpkg &#8211;initrd &#8211;append-to-version=-custom kernel_image kernel_headers
```

should generate the kernel headers also aswell as your initrd.
what guide have you followed?

regards,
Danny

-- edit -- 

just thought when I recompile the kernel I dont use fakeroot I use sudo, though I doubt this will make much difference.

---

### Post by danwood76 on 2008-01-30
also if you have built it in one directory as you should you can just do: (after the compile)
```
sudo dpkg -i *.deb
``` and this will install all the debs.

I think there is more than two in the build process.
Just make sure you delete the old *.debs before you start the build, or else the command I gave you above will install those aswell.

regards,
Danny

---

### Post by supertails on 2008-01-30
What will some of the old debs look like and how do I delete them one by one or by a group.

---

### Post by danwood76 on 2008-01-30
when your in that dir in terminal just type 
```
sudo rm *.deb
```

regards,
Danny

---

### Post by supertails on 2008-01-30
```
tails@tails-laptop:~$     $ uname -r
bash: $: command not found
tails@tails-laptop:~$ 
tails@tails-laptop:~$     2.6.17-10-generic
bash: 2.6.17-10-generic: command not found
tails@tails-laptop:~$ sudo apt-get install linux-source-2.6.17 kernel-package libncurses5-dev fakeroot
Reading package lists... Done
Building dependency tree... 50%






Building dependency tree... 96%
Building dependency tree       
Reading state information... Done





E: The package linux-image-2.6.24 needs to be reinstalled, but I can't find an archive for it.
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$ 
tails@tails-laptop:~$     $ dpkg -L linux-source-2.6.17
bash: $: command not found
tails@tails-laptop:~$     /.
bash: /.: is a directory
tails@tails-laptop:~$     /usr
bash: /usr: is a directory
tails@tails-laptop:~$     /usr/src
bash: /usr/src: is a directory
tails@tails-laptop:~$     /usr/src/linux-source-2.6.17.tar.bz2
bash: /usr/src/linux-source-2.6.17.tar.bz2: No such file or directory
tails@tails-laptop:~$     /usr/share
bash: /usr/share: is a directory
tails@tails-laptop:~$     /usr/share/doc
bash: /usr/share/doc: is a directory
tails@tails-laptop:~$     /usr/share/doc/linux-source-2.6.17
bash: /usr/share/doc/linux-source-2.6.17: No such file or directory
tails@tails-laptop:~$     (trimmed)
bash: trimmed: command not found
tails@tails-laptop:~$ 
tails@tails-laptop:~$ sudo /bin/bash
root@tails-laptop:~# cd /usr/src
root@tails-laptop:/usr/src# bunzip2 linux-source-2.6.17.tar.bz2
bunzip2: Can't open input file linux-source-2.6.17.tar.bz2: No such file or directory.
root@tails-laptop:/usr/src# 
root@tails-laptop:/usr/src# tar xvf linux-source-2.6.17.tar
tar: linux-source-2.6.17.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
root@tails-laptop:/usr/src# 
root@tails-laptop:/usr/src# ln -s linux-source-2.6.17 linux
ln: creating symbolic link `linux/linux-source-2.6.17' to `linux-source-2.6.17': File exists
root@tails-laptop:/usr/src# cp /boot/config-`uname -r` /usr/src/linux/.config
root@tails-laptop:/usr/src#     cd /usr/src/linux
root@tails-laptop:/usr/src/linux# 
root@tails-laptop:/usr/src/linux#     make menuconfig
scripts/kconfig/mconf arch/x86/Kconfig


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

root@tails-laptop:/usr/src/linux# make-kpkg clean
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean 

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-2.6.24'
====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||                     \
          mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=i386 distclean
make[2]: Entering directory `/usr/src/linux-2.6.24'
  CLEAN   arch/x86/boot/compressed
  CLEAN   arch/x86/boot
  CLEAN   /usr/src/linux-2.6.24
  CLEAN   arch/x86/kernel
  CLEAN   drivers/atm
  CLEAN   drivers/char
  CLEAN   drivers/eisa
  CLEAN   drivers/md
  CLEAN   drivers/net/wan
  CLEAN   drivers/scsi/aic7xxx
  CLEAN   drivers/scsi
  CLEAN   init
  CLEAN   lib
  CLEAN   sound/oss
  CLEAN   usr
  CLEAN   .tmp_versions
  CLEAN   vmlinux System.map .tmp_kallsyms1.o .tmp_kallsyms1.S .tmp_kallsyms2.o .tmp_kallsyms2.S .tmp_vmlinux1 .tmp_vmlinux2 .tmp_System.map
    dpkg -i linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb

    dpkg -i linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb

  CLEAN   scripts/basic
  CLEAN   scripts/genksyms
  CLEAN   scripts/kconfig
  CLEAN   scripts/mod
  CLEAN   /usr/src/linux-2.6.24/debian/
  CLEAN   scripts
  CLEAN   include/config
  CLEAN   .config .config.old include/asm .version include/linux/autoconf.h include/linux/version.h include/linux/utsrelease.h Module.symvers
make[2]: Leaving directory `/usr/src/linux-2.6.24'
test ! -f config.precious || mv -f config.precious .config
test ! -f stamp-patch || /usr/bin/make -f ./debian/rules unpatch_now
test -f stamp-building || test -f debian/official || rm -rf debian
# work around idiocy in recent kernel versions
test ! -e scripts/package/builddeb.dist || \
            mv -f scripts/package/builddeb.dist scripts/package/builddeb
test ! -e scripts/package/Makefile.dist || \
            mv -f scripts/package/Makefile.dist scripts/package/Makefile
rm -f modules/modversions.h modules/ksyms.ver debian/files conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches debian/buildinfo stamp-build stamp-configure stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-manual stamp-patch stamp-buildpackage stamp-debian stamp-arch-conf stamp-indep-conf stamp-configure-arch stamp-configure-indep stamp-configure stamp-arch-build stamp-indep-build stamp-build-arch stamp-build-indep stamp-build stamp-arch-inst stamp-indep-inst stamp-install stamp-install-arch stamp-install-indep stamp-arch-bin stamp-indep-bin stamp-binary stamp-binary-arch stamp-binary-indep debian/stamp-kernel-conf debian/stamp-prepare stamp-patch debian/stamp-conf stamp-debian debian/stamp-build-kernel stamp-buildpackage stamp-kernel-source stamp-kernel-manual stamp-kernel-doc stamp-kernel-headers stamp-kernel-image
rm -rf  /usr/src/linux/debian/tmp_man
make[1]: Leaving directory `/usr/src/linux-2.6.24'
====== making target CLN-indep [new prereqs: CLN-common]======

====== making target CLEAN/linux-source-2.6.24 [new prereqs: CLN-indep]======

rm -rf /usr/src/linux/debian/linux-source-2.6.24
====== making target CLEAN/linux-doc-2.6.24 [new prereqs: CLN-indep]======

rm -rf /usr/src/linux/debian/linux-doc-2.6.24
====== making target CLEAN/linux-manual-2.6.24 [new prereqs: CLN-indep]======

rm -rf /usr/src/linux/debian/linux-manual-2.6.24
====== making target clean-indep [new prereqs: linux-source-2.6.24 linux-doc-2.6.24 linux-manual-2.6.24]======
====== making target CLN-arch [new prereqs: CLN-common]======

====== making target CLEAN/linux-headers-2.6.24 [new prereqs: CLN-arch]======

rm -rf /usr/src/linux/debian/linux-headers-2.6.24
====== making target CLEAN/linux-image-2.6.24 [new prereqs: CLN-arch]======

rm -rf /usr/src/linux/debian/linux-image-2.6.24
test ! -d ./debian || test ! -e stamp-building ||            \
        sed -e 's/=V/2.6.24/g'    -e 's/=B//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's@=MK@@g' -e 's@=A@i386@g'   \
            -e 's/=I//g'     -e 's,=D,/boot,g'        \
            -e 's/=MD//g'                                \
            -e 's@=M@@g'    -e 's/=OF//g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
          ./debian/templates.in   > ./debian/templates.master
test ! -d ./debian || test ! -e stamp-building ||       po2debconf debian/templates.master > debian/templates
====== making target CLEAN/linux-uml-2.6.24 [new prereqs: CLN-arch]======

====== making target CLEAN/linux-xen0-2.6.24 [new prereqs: CLN-arch]======

====== making target CLEAN/linux-xenu-2.6.24 [new prereqs: CLN-arch]======

====== making target clean-arch [new prereqs: linux-headers-2.6.24 linux-image-2.6.24 linux-uml-2.6.24 linux-xen0-2.6.24 linux-xenu-2.6.24]======
====== making target stamp-clean [new prereqs: clean-indep clean-arch]======

rm -f  modules/modversions.h modules/ksyms.ver debian/files conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches debian/buildinfo stamp-build stamp-configure stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-manual stamp-patch stamp-buildpackage stamp-debian stamp-arch-conf stamp-indep-conf stamp-configure-arch stamp-configure-indep stamp-configure stamp-arch-build stamp-indep-build stamp-build-arch stamp-build-indep stamp-build stamp-arch-inst stamp-indep-inst stamp-install stamp-install-arch stamp-install-indep stamp-arch-bin stamp-indep-bin stamp-binary stamp-binary-arch stamp-binary-indep debian/stamp-kernel-conf debian/stamp-prepare stamp-patch debian/stamp-conf stamp-debian debian/stamp-build-kernel stamp-buildpackage stamp-kernel-source stamp-kernel-manual stamp-kernel-doc stamp-kernel-headers stamp-kernel-image
rm -rf  /usr/src/linux/debian/tmp_man
rm -f core TAGS                                                     \
               `find . ! -regex '.*/\.git/.*' ! -regex '.*/\{arch\}/.*'      \
                       ! -regex '.*/CVS/.*'   ! -regex '.*/\.arch-ids/.*'    \
                       ! -regex '.*/\.svn/.*'                                \
                   \( -name '*.orig' -o -name '*.rej' -o -name '*~'       -o \
                      -name '*.bak'  -o -name '#*#'   -o -name '.*.orig'  -o \
                      -name '.*.rej' -o -name '.SUMS' -o -size 0 \)          \
                -print`
====== making target clean [new prereqs: stamp-clean]======
root@tails-laptop:/usr/src/linux#     dpkg -i linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
dpkg: error processing linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
root@tails-laptop:/usr/src/linux# 
root@tails-laptop:/usr/src/linux#     dpkg -i linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
dpkg: error processing linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
root@tails-laptop:/usr/src/linux# 
root@tails-laptop:/usr/src/linux#     dpkg -i linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
dpkg: error processing linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
root@tails-laptop:/usr/src/linux# 
root@tails-laptop:/usr/src/linux#     dpkg -i linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
dpkg: error processing linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-headers-2.6.17.14-ubuntu1-custom_2.6.17.14-ubuntu1-custom-10.00.Custom_i386.deb
root@tails-laptop:/usr/src/linux#     uname -r
2.6.24
root@tails-laptop:/usr/src/linux# 
root@tails-laptop:/usr/src/linux#     2.6.17.14-ubuntu1-custom
bash: 2.6.17.14-ubuntu1-custom: command not found
root@tails-laptop:/usr/src/linux# fakeroot make-kpkg –initrd –append-to-version=-custom kernel_image kernel_headers
The program 'fakeroot' is currently not installed.  You can install it by typing:
apt-get install fakeroot
bash: fakeroot: command not found
root@tails-laptop:/usr/src/linux# sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
root@tails-laptop:/usr/src/linux# sudo rm *.deb
rm: cannot remove `*.deb': No such file or directory
root@tails-laptop:/usr/src/linux# 


```

---

### Post by danwood76 on 2008-01-30
You dont have the understanding of the linux command line to re compile the kernel.
If I were you I would load up the original gutsy kernel at grub and make it your default.

In the above example you exectute a command and it throws you an error, but in stead of re reading it you just go on to the next thing.

Your apt isnt working properly as you havent installed 2.6.24 properly in the first place.
If I were you I would try and compile some programs first and get to know the command line before trying to recompile the kernel.

regards,
Danny

---

### Post by supertails on 2008-01-30
I reinstalled the OS.

---

