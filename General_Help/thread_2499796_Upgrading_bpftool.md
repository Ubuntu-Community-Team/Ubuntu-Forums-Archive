---
title: "Upgrading bpftool"
date: 2024-08-11
forum: General Help
---

### Post by viru7 on 2024-08-11
I want to use bpftool with Ubuntu 22.04.  I think I need to install the following 3 packages for this: linux-tools-common, linux-tools-generic, and a kernel specific version such as linux-tools-5.15.0-25-generic.  This works.

However after an "apt upgrade" bpftool no longer works and asks me to install linux-tools for the new kernel such as linux-tools-6.5.0-45-generic.

Is it possible to set it up so that this is not necessary?  That is for the required version of ilink-tools for the kernel to automatically be installed on an apt upgrade?

---

### Post by him610 on 2024-08-11
> bpftool?
```
$ apt show bpftool
Package: bpftool
State: not a real package (virtual)
N: Can't select candidate version from package bpftool as it has no candidate
N: Can't select versions from package 'bpftool' as it is purely virtual
N: No packages found

```
If you let us know what your end objective is, maybe someone can suggest another package.

---

### Post by viru7 on 2024-08-11
Thanks for the reply.  I am using bpftool to load a BPF program into the kernel.  However this isn't really a bpftool question it's an apt question. 
Usually we expect that a system will keep working after running "apt update && apt upgrade".  In this case it doesn't, it need intervention to keep working.
Maybe this can't be avoided.  Clearly there needs to be a different bpf-tool for each kernel version and maybe there is no automatic mechanism in apt to keep that up to date.
Or possibly there is something I don't know that will keep it up to date.

---

### Post by deadflowr on 2024-08-11
Install linux-hwe-6.5-tools-common.
That will bring in bpftool and it lines up with the current kernel version for the 6.5 kernel stack.
It should also keep it up-to-date when any new 6.5 kernels are installed.


However...
Eventually expect it move up to linux-hwe-6.8-tools-common soon as the HWE kernel stack should be moving up to that version soon.
it may move up to it on it's own, but if it doesn't you might need to install it when the time comes.

---

### Post by viru7 on 2024-08-12
Thanks for the suggestion
Unfortunately in my testing, installing linux-hwe-6.5-tools-common did not bring in bpftool
I still need to install linux-tools-6.5.0-45-generic

---

### Post by deadflowr on 2024-08-12
Yeah, 
downloading and extacting both packages it looks like they've mixed up the two package informations.
As I see these
```
apt show linux-tools-6.5.0-45
Package: linux-tools-6.5.0-45-generic
Architecture: amd64
Version: 6.5.0-45.45~22.04.1
Priority: optional
Section: devel
Source: linux-hwe-6.5
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 474
Depends: linux-hwe-6.5-tools-6.5.0-45
Filename: pool/main/l/linux-hwe-6.5/linux-tools-6.5.0-45-generic_6.5.0-45.45~22.04.1_amd64.deb
Size: 1808
MD5sum: 2ee2c14284eed88ff4957eded759cd55
SHA1: dea0edf208c9ead53d87a413e9299d0b9229e78d
SHA256: 8b6e3afe0af4d4ff539fcd727d118fd347833dab27d4770f1690ab5b36fab8eb
SHA512: 1f18eedcad1e6716500aeb2313e09856bb8206fa239511bb9b2d1e8a4297ef3c3267111eb24a10b58e80d97aec4dce48c8a85328cc019cfd2ec24fee26992961
Description-en: Linux kernel version specific tools for version 6.5.0-45
 This package provides the architecture dependant parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0-45 on
 64 bit x86.
Description-md5: bc3da7db4e18d4109d4d03fbfd4b0293
```
This package contains the bpftool.

And
```
apt show linux-hwe-6.5-tools-common
Package: linux-hwe-6.5-tools-common
Architecture: all
Version: 6.5.0-45.45~22.04.1
Multi-Arch: foreign
Priority: optional
Section: kernel
Source: linux-hwe-6.5
Origin: Ubuntu
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 462
**Provides: bpftool**
Depends: lsb-release, hwdata
Filename: pool/main/l/linux-hwe-6.5/linux-hwe-6.5-tools-common_6.5.0-45.45~22.04.1_all.deb
Size: 103026
MD5sum: bf102d196affa2f4ccc66f3f7e7530f2
SHA1: 84701890bfc948cfbad4acbab589aa1d119a38df
SHA256: 984691a8aec044b51ab7b1cf069bc6785b11a97ea7393ed274d981ec45263c24
SHA512: 6add60d8ab75716b91ad812600bd12a1d7e5b503c2ef90fe84060b8d1132debd6a84afabd3d99b288d0d5f0f8f51706668879f5d8ceb79fe98c01239519491bd
Description-en: Linux kernel version specific tools for version 6.5.0
 This package provides the architecture independent parts for kernel
 version locked tools (such as perf and x86_energy_perf_policy) for
 version 6.5.0.
Description-md5: d1d42e0c0cef1f52a628b9ca6edfcedf
```
Show the bpftool listed as provided, but the package itself is basically empty.

---

