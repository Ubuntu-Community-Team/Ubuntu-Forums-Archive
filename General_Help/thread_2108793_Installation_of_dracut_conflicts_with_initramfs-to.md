---
title: "Installation of dracut conflicts with initramfs-tools"
date: 2013-01-25
forum: General Help
---

### Post by ffeldhaus on 2013-01-25
I just tried to install dracut, a replacement for the initramfs-tools on a fresh Ubuntu 12.10 server to use the advanced features of dracut for booting from NFS over two bonded interfaces. 

Unfortunately the installation encountered the following conflict:
```
root@ubuntu:~# aptitude install dracut
The following NEW packages will be installed:
  cryptsetup{a} cryptsetup-bin{a} dmraid{a} dracut{b} kpartx{a} kpartx-boot{a} libcryptsetup4{a} libdevmapper-event1.02.1{a} libdmraid1.0.0.rc16{a} libreadline5{a} lvm2{a} mdadm{a} postfix{a} ssl-cert{a} watershed{a} 
0 packages upgraded, 15 newly installed, 0 to remove and 2 not upgraded.
Need to get 3,004 kB of archives. After unpacking 8,428 kB will be used.
The following packages have unmet dependencies:
 dracut : Conflicts: initramfs-tools but 0.103ubuntu0.2 is installed.
          Conflicts: initramfs-tools:i386 which is a virtual package.
The following actions will resolve these dependencies:
     Keep the following packages at their current version:
1)     dracut [Not Installed]                             
Accept this solution? [Y/n/q/?] Y
``` 

The proposed solution "dracut [Not Installed]" does not help. Unfortunately I didn't find much information on dracut on Ubuntu so that I could identify if it should work. I found the following bug report in debian which is unsolved until now: 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=669342](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=669342)

I quickly tested the installation of dracut on a Ubuntu 12.04 server and it installed fine, but I need it for Ubuntu 12.10.

Can someone help me to install it and maybe share some insides on why it's so hard to use dracut in Ubuntu?

In an lwn.net article from 2009 dracut was presented as the tool which might ultimately harmonize the initial ramdisks of all linux distributions. As it seems to offers quite a few interesting features (e.g. advanced network setup and more options for the root fs) and is told speed up the boot process I'm curious to know if and when Ubuntu will adopt dracut as the primary tool for building initial ramdisks?

---

### Post by ffeldhaus on 2013-01-30
I rephrased the issue as a question and asked it on askUbuntu. The answer boils down to:
Dracut is not working with Ubuntu 12.10 and will not work with Ubuntu in the near future.

My question on askUbuntu can be found here:
- [How to install dracut on Ubuntu 12.10?]("http://askubuntu.com/questions/248970/how-to-install-dracut-on-ubuntu-12-10")
The corresponding bug report can be found here:
- [Package dracut cannot be installed on Ubuntu 12.10]("https://bugs.launchpad.net/ubuntu/+source/dracut/+bug/1108987")
The underlying issue is tracked in this bug:
- [Depend on linux-initramfs-tools]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1109029")

---

