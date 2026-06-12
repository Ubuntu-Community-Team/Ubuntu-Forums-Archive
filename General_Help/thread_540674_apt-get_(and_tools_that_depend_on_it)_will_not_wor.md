---
title: "apt-get (and tools that depend on it) will not work"
date: 2007-09-01
forum: General Help
---

### Post by .Michael on 2007-09-01
When I attempt to use apt-get, update my operating system or add/remove in the applications folder, it fails to do anything.

Heres what happens when I go to use it in the terminal:
```
michael@linux0:/usr/local/bin$ sudo apt-get install qemuPassword:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bochsbios vgabios
Recommended packages:
  debootstrap sharutils vde proll openhackware
The following NEW packages will be installed:
  bochsbios qemu vgabios
0 upgraded, 3 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/3706kB of archives.
After unpacking 10.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing /var/cache/apt/archives/vgabios_0.6a-1_all.deb (--unpack):
 files list file for package `xmodmap' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/vgabios_0.6a-1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@linux0:/usr/local/bin$ 
```

---

### Post by meierfra on 2007-09-01
I think the file  "var/lib/dpkg/info/xmodmap.list"
got corrupted. This link shows you how to fix the problem:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html]("https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html")

Let me know if you need more help.

---

