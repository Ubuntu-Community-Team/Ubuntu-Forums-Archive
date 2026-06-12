---
title: "I can not get perf on freshly installed 22.04.2 LTS"
date: 2023-07-04
forum: General Help
---

### Post by chickapachimecho on 2023-07-04
I have uname -r as 5.19.0-32-generic.
 I have tried to install linux-tools-5.19.0-32-generic, but that package does not exist.
 If I install linux-tools-common and linux-tools-generic, I get   linux-tools-5.15.0-76 and linux-tools-5.15.0-76-generic, but when I run   perf I get this output
> 
 WARNING: perf not found for kernel 5.19.0-32

  You may need to install the following packages for this specific kernel:
    linux-tools-5.19.0-32-generic
    linux-cloud-tools-5.19.0-32-generic

  You may also want to install one of the following packages to keep up to date:
    linux-tools-generic
    linux-cloud-tools-generic

 The package linux-tools-5.19.0-32-generic that does not exist and linux-tools-generic was already installed.
 Does Ubuntu not keep perf up-to-date? Can I build it from source and get it to work?
 I found perf headers in ../../linux-hwe-5.19-headers-5.19.0-32/tools/perf I tried to make it, but
> 
   BUILD:   Doing 'make -j8' parallel build
Makefile.perf:8: ../scripts/utilities.mak: No such file or directory
make[1]: *** No rule to make target '../scripts/utilities.mak'.  Stop.
make: *** [Makefile:70: all] Error 2

 and yea, that target does not exist.
Do I have to downgrade to get perf working?

---

### Post by chickapachimecho on 2023-07-04
Oh, I am using Desktop Pro Ubuntu 22.04.2 LTS

---

### Post by ian-weisser on 2023-07-04
In [https://askubuntu.com/questions/1476192](https://askubuntu.com/questions/1476192), you wrote that you have installed Fedora instead and thus apparently no longer seek an answer to this question.

---

### Post by MAFoElffen on 2023-07-05
??? How about that. LOL

I this person was still interested, and for others that read this later...
```

mafoelffen@Mikes-B460M:~$ apt-cache show linux-tools-$(uname -r)
Package: linux-tools-5.19.0-46-generic
Architecture: amd64
Version: 5.19.0-46.47~22.04.1
Priority: optional
Section: devel
Source: linux-hwe-5.19
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 496
Depends: linux-hwe-5.19-tools-5.19.0-46
Filename: pool/main/l/linux-hwe-5.19/linux-tools-5.19.0-46-generic_5.19.0-46.47~22.04.1_amd64.deb
Size: 1814
MD5sum: a92743669e6fbe8c4e83b50092cfabe3
SHA1: d070bc4acd0a59dc182971b5e4ee0f464b654d86
SHA256: c5381fbbd52d7ed992b2f4162220be1c6b288e0514829e0198f4fed50e950ea3
SHA512: 5e0333f03028ff9f6ee05c0ac3795cc9e9e1fdcfc0935cef640e1489977f268868e27f6b6e4210ee1a7282de3c24a945164d87bf942625602ec1ad32016049b7
Description-en: Linux kernel version specific tools for version 5.19.0-46
 This package provides the architecture dependant parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 5.19.0-46 on
 64 bit x86.
Description-md5: 8608a1e8a1dc661d6b0e479cd1544dfb

mafoelffen@Mikes-B460M:~$ sudo apt install -y -s linux-tools-$(uname -r)
[sudo] password for mafoelffen: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  libzbd2
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  linux-hwe-5.19-tools-5.19.0-46 linux-tools-common
The following NEW packages will be installed:
  linux-hwe-5.19-tools-5.19.0-46 linux-tools-5.19.0-46-generic linux-tools-common
0 upgraded, 3 newly installed, 0 to remove and 6 not upgraded.
Inst linux-tools-common (5.15.0-76.83 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [all])
Inst linux-hwe-5.19-tools-5.19.0-46 (5.19.0-46.47~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst linux-tools-5.19.0-46-generic (5.19.0-46.47~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf linux-tools-common (5.15.0-76.83 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [all])
Conf linux-hwe-5.19-tools-5.19.0-46 (5.19.0-46.47~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf linux-tools-5.19.0-46-generic (5.19.0-46.47~22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])

```

---

