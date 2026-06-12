---
title: "Can't load kvm_intel"
date: 2008-04-28
forum: General Help
---

### Post by jjrev on 2008-04-28
I'm running 64bit Hardy (8.04) on a system with two X5472 (64bit Xeon).  I can't load the kvm_intel module.

Here are some details:

$ sudo apt-get install kvm libvirt-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
debootstrap etherboot kvm-source
Recommended packages:
vde2
The following NEW packages will be installed:
kvm libvirt-bin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/858kB of archives.
After this operation, 2961kB of additional disk space will be used.
Selecting previously deselected package kvm.
(Reading database ... 97251 files and directories currently installed.)
Unpacking kvm (from .../kvm_1%3a62+dfsg-0ubuntu7_amd64.deb) ...
kvm: Using the existing group "kvm" (gid 125) for /dev/kvm
Selecting previously deselected package libvirt-bin.
Unpacking libvirt-bin (from .../libvirt-bin_0.4.0-2ubuntu8_amd64.deb) ...
Setting up kvm (1:62+dfsg-0ubuntu7) ...
[COLOR="Red"]FATAL: Error inserting kvm_intel (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported
* Module kvm_intel failed to load
invoke-rc.d: initscript kvm, action "start" failed.[/COLOR]

Setting up libvirt-bin (0.4.0-2ubuntu ...
* Starting libvirt management daemon libvirtd [ OK ]

---

### Post by capitol on 2008-09-11
I have the same problem, this is what my dmesg says:

[861011.504717] kvm: disabled by bios

---

### Post by abreslav on 2008-10-01
I do experience this problem too: Ubuntu Hardy on Thinkpad T60, VT suuport is enabled in BIOS

---

### Post by Sycron on 2008-10-01
Can you succesfully run ```
sudo modprobe kvm_intel
```

---

