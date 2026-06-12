---
title: "does the kernel read the Intel-microcode automatically?"
date: 2019-06-12
forum: General Help
---

### Post by &amp;wP*!) on 2019-06-12
I have a microcode but am not sure whether it is loaded.

Following command says that I have the most up-to-date Ubuntu package version of the microcode:
```
$ apt-cache policy intel-microcode
intel-microcode:
[B]  Installed: 3.20190514.0ubuntu0.19.04.3
  Candidate: 3.20190514.0ubuntu0.19.04.3[/B]
  Version table:
 *** 3.20190514.0ubuntu0.19.04.3 500
        500 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu disco-security/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20190312.1 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
```
Following command shows that the package above originates from a version 3.20190312.1:
```
$ apt-cache show intel-microcode 
Package: intel-microcode
Architecture: amd64
**Version: 3.20190514.0ubuntu0.19.04.3**
Priority: extra
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Henrique de Moraes Holschuh <hmh@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 2542
Depends: iucode-tool (>= 1.0)
Recommends: initramfs-tools (>= 0.113~)
Conflicts: microcode.ctl (<< 0.18~0)
Filename: pool/main/i/intel-microcode/intel-microcode_3.20190514.0ubuntu0.19.04.3_amd64.deb
Size: 2047732
**MD5sum: 813c4b873df9ede64128f7527b266155**
SHA1: 2b00b8b6f7ea9734ef6746f3a56e61980b49a57d
SHA256: 93f8f110ebbe04196eb5dcebfa5107eefd903a58b2a19ed3579e9edfe3d71560
Homepage: https://downloadcenter.intel.com/search?keyword=linux+microcode
Description-en: Processor microcode firmware for Intel CPUs
 This package contains updated system processor microcode for
 Intel i686 and Intel X86-64 processors.  Intel releases microcode
 updates to correct processor behavior as documented in the
 respective processor specification updates.
 .
 For AMD processors, please refer to the amd64-microcode package.
**Description-md5: 3edb9824276886579313f0e847f6bb14**
Supported: 9m

Package: intel-microcode
Architecture: amd64
**Version: 3.20190312.1**
Priority: extra
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Henrique de Moraes Holschuh <hmh@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 2075
Depends: iucode-tool (>= 1.0)
Recommends: initramfs-tools (>= 0.113~)
Conflicts: microcode.ctl (<< 0.18~0)
Filename: pool/main/i/intel-microcode/intel-microcode_3.20190312.1_amd64.deb
Size: 1749016
**MD5sum: 184231cd4b53f73d9d8e6de7ab902920**
SHA1: 7376feec6b4028f9a138f37097db996e81bcc55f
SHA256: eb906af7f88c2bb3f2be3ca242fbbdaeb26a8469a4807a7d514dfe85428c6615
Homepage: https://downloadcenter.intel.com/search?keyword=linux+microcode
Description-en: Processor microcode firmware for Intel CPUs
 This package contains updated system processor microcode for
 Intel i686 and Intel X86-64 processors.  Intel releases microcode
 updates to correct processor behavior as documented in the
 respective processor specification updates.
 .
 For AMD processors, please refer to the amd64-microcode package.
**Description-md5: 3edb9824276886579313f0e847f6bb14**
Supported: 9m
```
[The latest Intel microcode from Intel portal]("https://downloadcenter.intel.com/download/28727/Linux-Processor-Microcode-Data-File") shows the same version but the MD5 does not match any MD5 above:
```
Linux* Processor Microcode Data File
Version: 20190312 (Latest) Date: 3/12/2019
**MD5: edc254719a003f88f6d98b9ac34fe156**
```
dmesg says a microcode is loaded but its timestamp is not 2019.03.12, nor I can find signature, pf and revision hex codes in the [release notes of Intel microcode github]("https://github.com/intel/Intel-Linux-Processor-Microcode-Data-Files/blob/master/releasenote"):
```
$ dmesg | grep microcode
[    0.000000] microcode: microcode updated early to revision 0x25, date = 2019-02-26
[    1.117117] microcode: sig=0x40651, pf=0x40, revision=0x25
[    1.117834] microcode: Microcode Update Driver: v2.2.
```
Grub file **/boot/grub/grub.cfg** does not contain any microcode upload
```
linux   /@/boot/**vmlinuz-5.0.0-16-generic** root=UUID=nnnn... ro rootflags=subvol=@  text resume=UUID=nnn....
initrd  /@/boot/**initrd.img-5.0.0-16-generic**
```
Intel microcode, however is dependency to the kernel version above:
```
$ apt-cache rdepends intel-microcode
intel-microcode
Reverse Depends:
  iucode-tool
  linux-image-oem
  linux-image-lowlatency
  linux-image-generic
  microcode.ctl
  microcode.ctl
  needrestart
  linux-image-oem
  linux-image-lowlatency
**  linux-image-generic**
  amd64-microcode
$ apt-cache depends linux-image-generic
linux-image-generic
**  Depends: linux-image-5.0.0-16-generic**
  Depends: linux-modules-extra-5.0.0-16-generic
  Depends: linux-firmware
  Depends: intel-microcode
  Depends: amd64-microcode
  Recommends: thermald
```
**Question:** does the kernel above automatically load the installed microcode package or not?

---

### Post by deadflowr on 2019-06-12
Yes you're using the revisioned version proper for your architecture.

While the package has been updated your system can only currently use the revision shown (0x25), which was created on 2-26-2019.

Different revisions build for different processors, and processor families.
When you boot the system reads the processor info then loads the microcode from the proper firmware file(s) in /lib/firmware/intel-ucode.

The microcode package isn't one monolithic file but many files which cover the many processors and families. Each file can represent a different revision.
It's revision will have it's own timestamp unrelated to the current packaging timestamps.

The md5sum output will differ because one is intel's original package and the other is Ubuntu repackaging it.

---

### Post by &amp;wP*!) on 2019-06-12
> **deadflowr said:**
> Yes you're using the revisioned version proper for your architecture.
The dmesg messages are the 1st ones during boot, which tells me that this is early loading (microcode is in initrd).
intel-microcode can be loaded only during late-loading. During late-loading stage I had expected messages like "updated" in dmesg, but there isn't:
```
$ dmesg | egrep 'microcode|update' 
[    0.000000] microcode: microcode updated early to revision 0x25, date = 2019-02-26
[    0.000059] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.002248] e820: update [mem 0xdd000000-0xffffffff] usable ==> reserved
[    0.113908] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    1.117117] microcode: sig=0x40651, pf=0x40, revision=0x25
[    1.117834] microcode: Microcode Update Driver: v2.2.

```
The microcode information in early and late loading stages are the same, i.e. the one in initrd and the one in /lib/firmware (from intel-microcode package) are the same.

One way to find which file in /lib/firmware/intel-ucode belongs to which CPU, is described [here]("http://www.linuxfromscratch.org/blfs/view/svn/postlfs/firmware.html").
```
$ head -n7 /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 69
model name      : Intel(R) Core(TM) i7-4600U CPU @ 2.10GHz
stepping        : 1
microcode       : 0x25
```

so, 6, 69, 1 converted into hex gives  06-45-01, which file is [COLOR="#FF0000"]**below**[/COLOR]
```
$ ls -l /lib/firmware/intel-ucode/
total 2572
-rw-r--r-- 1 root root   8192 Mai 21 07:08 06-0f-02
-rw-r--r-- 1 root root  12288 Mai 21 07:08 06-0f-06
-rw-r--r-- 1 root root   8192 Mai 21 07:08 06-0f-07
-rw-r--r-- 1 root root   4096 Mai 21 07:08 06-0f-0a
-rw-r--r-- 1 root root  28672 Mai 21 07:08 06-0f-0b
-rw-r--r-- 1 root root  12288 Mai 21 07:08 06-0f-0d
-rw-r--r-- 1 root root  16384 Mai 21 07:08 06-16-01
-rw-r--r-- 1 root root  20480 Mai 21 07:08 06-17-06
-rw-r--r-- 1 root root   4096 Mai 21 07:08 06-17-07
-rw-r--r-- 1 root root  24576 Mai 21 07:08 06-17-0a
-rw-r--r-- 1 root root  14336 Mai 21 07:08 06-1a-04
-rw-r--r-- 1 root root  12288 Mai 21 07:08 06-1a-05
-rw-r--r-- 1 root root  15360 Mai 21 07:08 06-1c-02
-rw-r--r-- 1 root root  20480 Mai 21 07:08 06-1c-0a
-rw-r--r-- 1 root root   4096 Mai 21 07:08 06-1d-01
-rw-r--r-- 1 root root   9216 Mai 21 07:08 06-1e-05
-rw-r--r-- 1 root root   9216 Mai 21 07:08 06-25-02
-rw-r--r-- 1 root root   4096 Mai 21 07:08 06-25-05
-rw-r--r-- 1 root root  12288 Mai 21 07:08 06-2a-07
-rw-r--r-- 1 root root  11264 Mai 21 07:08 06-2c-02
-rw-r--r-- 1 root root  18432 Mai 21 07:08 06-2d-06
-rw-r--r-- 1 root root  19456 Mai 21 07:08 06-2d-07
-rw-r--r-- 1 root root   9216 Mai 21 07:08 06-2e-06
-rw-r--r-- 1 root root  14336 Mai 21 07:08 06-2f-02
-rw-r--r-- 1 root root 104448 Mai 21 07:08 06-37-08
-rw-r--r-- 1 root root  52224 Mai 21 07:08 06-37-09
-rw-r--r-- 1 root root  14336 Mai 21 07:08 06-3a-09.initramfs
-rw-r--r-- 1 root root  23552 Mai 21 07:08 06-3c-03.initramfs
-rw-r--r-- 1 root root  19456 Mai 21 07:08 06-3d-04.initramfs
-rw-r--r-- 1 root root  16384 Mai 21 07:08 06-3e-04
-rw-r--r-- 1 root root  11264 Mai 21 07:08 06-3e-06
-rw-r--r-- 1 root root  17408 Mai 21 07:08 06-3e-07
-rw-r--r-- 1 root root  34816 Mai 21 07:08 06-3f-02.initramfs
-rw-r--r-- 1 root root  18432 Mai 21 07:08 06-3f-04.initramfs
**[COLOR="#FF0000"]-rw-r--r-- 1 root root  21504 Mai 21 07:08 06-45-01.initramfs[/COLOR]**
-rw-r--r-- 1 root root  25600 Mai 21 07:08 06-46-01.initramfs
-rw-r--r-- 1 root root  14336 Mai 21 07:08 06-47-01.initramfs
-rw-r--r-- 1 root root  69632 Mai 21 07:08 06-4c-03
-rw-r--r-- 1 root root  68608 Mai 21 07:08 06-4c-04
-rw-r--r-- 1 root root 100352 Mai 21 07:08 06-4e-03
-rw-r--r-- 1 root root  30720 Mai 21 07:08 06-4f-01.initramfs
-rw-r--r-- 1 root root  30720 Mai 21 07:08 06-55-03
-rw-r--r-- 1 root root  32768 Mai 21 07:08 06-55-04
-rw-r--r-- 1 root root  47104 Mai 21 07:08 06-55-05
-rw-r--r-- 1 root root  47104 Mai 21 07:08 06-55-06
-rw-r--r-- 1 root root  47104 Mai 21 07:08 06-55-07
-rw-r--r-- 1 root root  32768 Mai 21 07:08 06-56-02.initramfs
-rw-r--r-- 1 root root  24576 Mai 21 07:08 06-56-03
-rw-r--r-- 1 root root  23552 Mai 21 07:08 06-56-04
-rw-r--r-- 1 root root  19456 Mai 21 07:08 06-56-05
-rw-r--r-- 1 root root  15360 Mai 21 07:08 06-5c-02
-rw-r--r-- 1 root root  17408 Mai 21 07:08 06-5c-09
-rw-r--r-- 1 root root  15360 Mai 21 07:08 06-5c-0a
-rw-r--r-- 1 root root 100352 Mai 21 07:08 06-5e-03
-rw-r--r-- 1 root root  11264 Mai 21 07:08 06-5f-01
-rw-r--r-- 1 root root  73728 Mai 21 07:08 06-7a-01
-rw-r--r-- 1 root root 197632 Mai 21 07:08 06-8e-09
-rw-r--r-- 1 root root  99328 Mai 21 07:08 06-8e-0a
-rw-r--r-- 1 root root  98304 Mai 21 07:08 06-8e-0b
-rw-r--r-- 1 root root  97280 Mai 21 07:08 06-8e-0c
-rw-r--r-- 1 root root  99328 Mai 21 07:08 06-9e-09
-rw-r--r-- 1 root root  98304 Mai 21 07:08 06-9e-0a
-rw-r--r-- 1 root root  99328 Mai 21 07:08 06-9e-0b
-rw-r--r-- 1 root root  98304 Mai 21 07:08 06-9e-0c
-rw-r--r-- 1 root root  97280 Mai 21 07:08 06-9e-0d
-rw-r--r-- 1 root root   7168 Mai 21 07:08 0f-03-04
-rw-r--r-- 1 root root  10240 Mai 21 07:08 0f-04-01
-rw-r--r-- 1 root root   2048 Mai 21 07:08 0f-04-03
-rw-r--r-- 1 root root   3072 Mai 21 07:08 0f-04-04
-rw-r--r-- 1 root root   3072 Mai 21 07:08 0f-04-07
-rw-r--r-- 1 root root   9216 Mai 21 07:08 0f-04-08
-rw-r--r-- 1 root root   2048 Mai 21 07:08 0f-04-09
-rw-r--r-- 1 root root   4096 Mai 21 07:08 0f-04-0a
-rw-r--r-- 1 root root   3072 Mai 21 07:08 0f-06-02
-rw-r--r-- 1 root root   6144 Mai 21 07:08 0f-06-04
-rw-r--r-- 1 root root   4096 Mai 21 07:08 0f-06-05
-rw-r--r-- 1 root root   2048 Mai 21 07:08 0f-06-08
```
Intel original files in github do not have the extension "initramfs".  These filenames were modified probably by Ubuntu team to prepare kernel and initrd for 5.0.0-16.

During boot microcode files in /lib/firmware are not read (no late loading), but the microcode in the kernel is used (early loading). 
It is because both versions are the same thus boot ignores the /lib/firmware.
But why there is no more verbose message in the boot phase about it? (something like "microcode in /lib/firmware is the same as in initrd, skipping...")

My assumption is intel-microcode package is redundant (it is already in the initrd of 5.0.0-16) for this setup.

I have tried to remove this package but APT tries to remove the kernel as well, therefore haven't done it:
```
$ sudo apt-get purge --auto-remove intel-microcode
[sudo] password for ...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amd64-microcode* intel-microcode* iucode-tool* linux-generic* linux-headers-generic* linux-image-generic*
  linux-signed-generic* thermald*
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
After this operation, 3.434 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
$ sudo apt-get remove intel-microcode
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode iucode-tool linux-headers-generic thermald
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  intel-microcode linux-generic linux-image-generic linux-signed-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 2.649 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
```

---

### Post by deadflowr on 2019-06-12
Yeah, the microcode package is now a dependency of linux-meta/linux-generic/linux-image-generic package
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259")
As noted you also have amd64-microcode installed.
Fun stuff.

---

### Post by &amp;wP*!) on 2019-06-12
> **deadflowr said:**
> Yeah, the microcode package is now a dependency of linux-meta/linux-generic/linux-image-generic package
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259")
As noted you also have amd64-microcode installed.
Fun stuff.

Thank you for the confirmation and for double-check :)

I set this to SOLVED.

---

