---
title: "libpam.so.0 incompatible with Checkpoint VPN in Ubuntu 12.10."
date: 2012-11-02
forum: General Help
---

### Post by deckard1 on 2012-11-02
I need to run the Checkpoint VPN SSL Network Extender (snx) in 64-bit Ubuntu. After installing it always complains about libpam.so.0:

```
snx: error while loading shared libraries: libpam.so.0: cannot open shared object file: No such file or directory
```

The way to make it work is to download and install the i386 version of libpam0g (libpam0g_1.1.3-7ubuntu2_i386.deb).

This worked fine in previous versions of ubuntu (up to 12.04), however in Ubuntu 12.10 I get this message when installing libpam0g:

```
Selecting previously unselected package libpam0g:i386.
(Reading database ... 165687 files and directories currently installed.)
Unpacking libpam0g:i386 (from libpam0g_1.1.3-7ubuntu2_i386.deb) ...
De-configuring libpam0g:amd64 ...
dpkg: error processing libpam0g:i386 (--install):
 package libpam0g:i386 1.1.3-7ubuntu2 cannot be configured because libpam0g:amd64 is at a different version (1.1.3-7ubuntu3)
dpkg: error processing libpam0g:amd64 (--install):
 package libpam0g:amd64 1.1.3-7ubuntu3 cannot be configured because libpam0g:i386 is at a different version (1.1.3-7ubuntu2)
Errors were encountered while processing:
 libpam0g:i386
 libpam0g:amd64

```

Synaptic also tells me I have two broken packages on my system.

There is a newer version of the file (libpam0g_1.1.3-7ubuntu3_i386.deb) that does not cause the broken package problem, however with that installed instead, Checkpoint still complains about libpam.so.0 and does not work.

Please help.

---

### Post by deckard1 on 2012-11-23
> **fukinregistration said:**
> This will fix your problem

sudo apt-get install libpam0g:i386

:guitar:

Thanks for the reply. Unfortunately it doesn't work. This installs version "1.1.3-7ubuntu3" of libpam0g from the repository, and snx still complains:

```

me@mypc:~$ sudo apt-get install libpam0g:i386
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libpam-doc:i386
The following NEW packages will be installed:
  libpam0g:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/61.2 kB of archives.
After this operation, 218 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package libpam0g:i386.
(Reading database ... 203603 files and directories currently installed.)
Unpacking libpam0g:i386 (from .../libpam0g_1.1.3-7ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libpam0g_1.1.3-7ubuntu3_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libpam0g/changelog.Debian.gz', which is different from other instances of package libpam0g:i386
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libpam0g_1.1.3-7ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
me@mypc:~$ snx -h
snx: error while loading shared libraries: libpam.so.0: cannot open shared object file: No such file or directory

```

snx does work with libpam0g version "1.1.3-7ubuntu2" installed, but that package is not compatible with Ubuntu 12.10.

---

