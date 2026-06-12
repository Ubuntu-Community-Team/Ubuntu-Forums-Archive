---
title: "latest update broken Dependency on Edgy for glibc6?"
date: 2007-01-24
forum: General Help
---

### Post by lorenco on 2007-01-24
After downloading the latest update I can't do and APT actions...

I get the following message:

> Preconfiguring packages ...
(Reading database ... 168137 files and directories currently installed.)
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


Any ideas what I can do here ?:mad:

---

### Post by lorenco on 2007-01-24
[http://ubuntuforums.org/showthread.php?p=2056901#post2056901](http://ubuntuforums.org/showthread.php?p=2056901#post2056901)

I Reckon this is related.... I also have build essential installed.

---

### Post by WW on 2007-01-24
A similar problem is reported here:
   [http://ubuntuforums.org/showthread.php?t=344570](http://ubuntuforums.org/showthread.php?t=344570)
That thread also gives a work-around.

---

### Post by cjwatson on 2007-01-24
We are investigating this, but cannot reproduce this specific form of the breakage involving libdl. Could you please let us know what unusual things you have installed on your system, over and above the ordinary desktop installation?

---

### Post by lorenco on 2007-01-24
I'll update the [bug report]("https://launchpad.net/ubuntu/+source/glibc/+bug/81125") with my details 
apt-sources and installed packages....

---

