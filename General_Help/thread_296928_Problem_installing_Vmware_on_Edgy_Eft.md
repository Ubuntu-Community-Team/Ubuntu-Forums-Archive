---
title: "Problem installing Vmware on Edgy Eft"
date: 2006-11-10
forum: General Help
---

### Post by sjpritch25 on 2006-11-10
I get the following error when i try installing vmware.

> Unable to find any instance of the super-server "inetd" or "xinetd". It is
possible that you do not have one of these packages installed on this machine.
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run
/usr/bin/vmware-config.pl after you fix the super-server.


I used apt-get to install inetd. here is that.

> stefan@stefan-desktop:/tmp/vmware-server-distrib$ sudo apt-get install inetd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting inetutils-inetd instead of inetd
The following packages were automatically installed and are no longer required:
vmware-player-kernel-modules-2.6.17-10 vmware-player-kernel-modules
libssl0.9.7
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
inetutils-inetd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.7kB of archives.
After unpacking 139kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe inetutils-inetd 2:1.4.3+20051212-4 [39.7kB]
Fetched 39.7kB in 0s (49.8kB/s)
Selecting previously deselected package inetutils-inetd.
(Reading database ... 103494 files and directories currently installed.)
Unpacking inetutils-inetd (from .../inetutils-inetd_2%3a1.4.3+20051212-4_i386.deb) ...
Setting up inetutils-inetd (1.4.3+20051212-4) ...
* Starting internet superserver inetd [ ok ] 

I used sudo-apt-get autoremove to remove the following

[B]vmware-player-kernel-modules-2.6.17-10
vmware-player-kernel-modules
libssl0.9.7[/B]

Thanks in Advance.

---

### Post by dad311 on 2006-11-10
Checkout this Howto:
[http://doc.gwos.org/index.php/VMWareXP](http://doc.gwos.org/index.php/VMWareXP)

Did you do "sudo apt-get install linux-headers-`uname -r` build-essential xinetd" ?

---

### Post by sjpritch25 on 2006-11-10
Thanks, i just needed **apt-get install build-essential xinetd**

---

