---
title: "[resolved] Captive Problems"
date: 2004-11-21
forum: General Help
---

### Post by Gibbz on 2004-11-21
ok im trying to install captive heres wht it shows the problem is, how do i fix it?




root@fabian:/home/fabian # /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-3-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-3-386/kernel/fs/lufs
Failed to find kernel headers for 2.6.8.1-3-386
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-3-386.
No Linux kernel sources for your running kernel were found.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-3-386/build
                /usr/src/kernel-headers-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-3-386

---

### Post by Gibbz on 2004-11-21
damn clicked resolved to early :(

anyway it seems to freeze when trying to mount using captive :(

---

### Post by ibs on 2004-12-16
same problem here.

---

### Post by jdong on 2004-12-16
You need to install the linux-headers package for your kernel. Browse linux-header with Synaptic, pick the one that matches your kernel version.

---

### Post by theh0g on 2004-12-16
I've just managed to get it to work and copying files to my NTFS partition works :) But I had to do /usr/share/lufs/prepmod and it only worked after I installed 2.6.9 686 kernel + headers.

---

### Post by badriram on 2005-01-05
[QUOTE=ibs]same problem here.[/QUOTE]
 After installing i had the same problem of it freezing, but after reading the syslog errors and some investigating i found out that i needed to create a user and group named captive. Once i did that everything worked like a charm.

Hope this helps

[thread=10175]Here is the howto...[/thread]

---

