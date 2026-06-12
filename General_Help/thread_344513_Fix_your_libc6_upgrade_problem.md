---
title: "Fix your libc6 upgrade problem"
date: 2007-01-23
forum: General Help
---

### Post by bwhite82 on 2007-01-23
If, like I did, you have a problem upgrading to that latest libc6 package, use the following to resolve the issue:

> sudo mkdir /usr/lib/temp
sudo mv /usr/lib/libpthread* /usr/lib/temp/
sudo apt-get install -f
sudo apt-get upgrade
sudo mv /usr/lib/temp/* /usr/lib

I searched half the internet looking for a solution and happened upon this and it worked for me. Cheers.

---

### Post by kb3hkg on 2007-01-23
this is not working for me here is the output I get after sudo apt-get install -f

Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.2_i386.deb) ...
Matching libraries: /usr/lib/libdl.so.2 /lib/ld-linux.so.2

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mdz on 2007-01-24
> **soldierboy101st said:**
> If, like I did, you have a problem upgrading to that latest libc6 package, use the following to resolve the issue:



I searched half the internet looking for a solution and happened upon this and it worked for me. Cheers.

A second update is being released which works around this problem for affected users, who should wait for it rather than following instructions like this (which can cause a number of unpleasant problems much worse than the original).  Techical details are available at [https://launchpad.net/bugs/81125](https://launchpad.net/bugs/81125)

---

