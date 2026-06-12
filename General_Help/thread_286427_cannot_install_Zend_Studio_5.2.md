---
title: "cannot install Zend Studio 5.2"
date: 2006-10-27
forum: General Help
---

### Post by OneSeventeen on 2006-10-27
After upgrading to edgy, I noticed I couldn't use Zend Studio anymore, but that's not surprising... I had to reinstall it after almost every kernel upgrade so this wasn't a big deal.

When I run the install, this is the output I get:> Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6989/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

Any ideas what could be causing this?  I use this application on a daily basis for my business, and I'll be booting windows to use it until I find a solution :(

---

### Post by TitanKing on 2006-10-28
> **OneSeventeen said:**
> After upgrading to edgy, I noticed I couldn't use Zend Studio anymore, but that's not surprising... I had to reinstall it after almost every kernel upgrade so this wasn't a big deal.

When I run the install, this is the output I get:

Any ideas what could be causing this?  I use this application on a daily basis for my business, and I'll be booting windows to use it until I find a solution :(

Yip same problem here, this seems to be in Edgy !

---

### Post by TitanKing on 2006-10-28
Symptoms

When trying to install Zend Studio Client or Zend SafeGuard 4.0 on various Linux systems, namely on Gentoo Linux and Fedora Core 5.0 (also may happen in Suse 10.x) , the installer crashes with the following errors thrown into the terminal:

awk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.17548/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

Cause


This problem is caused due to incompatibility of the installer's Java Run-time Environment with certain system libraries.

Resolution


After extracting the installer, run the following commands in a terminal directory on the same directory where you extracted the installer:

[PHP]
$ cp ZendStudio-5_2_0.bin ZendStudio-5_2_0.bin.bak

$ cat ZendStudio-5_2_0.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > ZendStudio-5_2_0.bin[/PHP]



Note: If you are installing Zend Studio Client, replace all occurrences of "ZendSafeGuard-4_0_0.bin" with "ZendStudio-5_1_0.bin" or "ZendStudio-X_X_X.bin" if you are installing a different version.

After the installation is complete, you can delete both the installer and the installer's .bak file.

Zend Studio Client specific notes


The same problem might also happen when trying to execute Zend Studio Client after the installation. In order to solve this, run the same commands on the {Zend Studio Installation Dir}/bin/ZDE file:

[PHP]
$ cd /usr/local/Zend/ZendStudioClient-5.1.0/bin
$ cp ZDE ZDE.bak
$ cat ZDE.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > ZDE
$ rm ZDE.bak[/PHP]

The above worked for me...

---

### Post by OneSeventeen on 2006-10-28
Cool, I'll try that... the Zend Development Environment after installing gives me the same errors, so the top half helped, but I haven't tried the bottom half yet.. I'll post back shortly.

I think I'll be wiping clean and starting over anyway... upgrades never go well for me, and half my applications work fine, until 30 minutes pass then programs stop opening when I click on them....

---

