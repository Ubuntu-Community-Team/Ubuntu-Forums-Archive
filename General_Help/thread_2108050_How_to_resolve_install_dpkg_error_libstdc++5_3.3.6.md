---
title: "How to resolve install dpkg error: libstdc++5_3.3.6-17ubuntu1_i386.deb"
date: 2013-01-23
forum: General Help
---

### Post by MelUbu on 2013-01-23
Hello.  Would someone help me troubleshoot the following pkg error? I am working on doing an oracle rdbms software install on my laptop running ubuntu 12.04.

here's specs on my laptop:
Linux 3.2.0-36-generic #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu 12.04.1

4gb RAM

vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz

I did a wget to get this pkg here:
wget [http://old-releases.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb](http://old-releases.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb)

Then I tried to to install, but getting the following error when running this command:
$ sudo dpkg --force-architecture -i libstdc++5_3.3.6-17ubuntu1_i386.deb

dpkg: warning: downgrading libstdc++5:i386 from 1:3.3.6-25ubuntu1 to 1:3.3.6-17ubuntu1.
dpkg: error processing libstdc++5_3.3.6-17ubuntu1_i386.deb (--install):
 libstdc++5:i386 1:3.3.6-17ubuntu1 (Multi-Arch: no) is not co-installable with libstdc++5:amd64 1:3.3.6-25ubuntu1 (Multi-Arch: same) which is currently installed
Errors were encountered while processing:
 libstdc++5_3.3.6-17ubuntu1_i386.deb

---

