---
title: "apt-get gone crazy: &quot;Cannot get debconf version. Is debconf installed?&quot;"
date: 2006-10-12
forum: General Help
---

### Post by Wesslan on 2006-10-12
Whenever I try to do anything with apt-get in my Ubuntu 6.06-box, I'll get the following error:

```

apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/4588kB of archives.
After unpacking 10.2MB of additional disk space will be used.
Do you want to continue [Y/n]?
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ... 2318 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.3.6-0ubuntu20_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !
dpkg: error processing /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does anyone have a clue what to do about it?
I've searched and found some threads about this problem but no solution. :(

Rgds,
Peter

---

### Post by Wesslan on 2006-10-13
Well, I kinda of solved it.
I found and backup och the status file in /var/lib/dpgk_status and used that one. It was a week old so my dependencies are problably not so fine but it is working... :)

---

