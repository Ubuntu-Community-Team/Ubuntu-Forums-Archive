---
title: "Unable to Locate package (libcap)"
date: 2017-02-20
forum: General Help
---

### Post by takashii42 on 2017-02-20
Each time I attempt to install libcap I get this error:

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsqlite3-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sqlite3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libpcap0.8-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libpcap0.8

E: Unable to locate package libpcap-dev
E: Package 'sqlite3' has no installation candidate
E: Package 'libsqlite3-dev' has no installation candidate
E: Package 'libpcap0.8-dev' has no installation candidate[/HTML]

I am running this code:

[HTML]sudo apt-get install libpcap0.8 libpcap0.8-dev libpcap-dev[/HTML]

I am unning Ubuntu 16.04 from a USB bootloader on my Mac

---

### Post by #&amp;thj^% on 2017-02-20
I would double check your sources in "/etc/apt/sources.list"
They are all there.
Mine:
```
$ apt policy libpcap0.8 libpcap0.8-dev libpcap-dev
libpcap0.8:
[COLOR=#ff0000]  Installed: 1.7.4-2[/COLOR]
  Candidate: 1.7.4-2
  Version table:
 *** 1.7.4-2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libpcap0.8-dev:
[COLOR=#ff0000]  Installed: 1.7.4-2[/COLOR]
  Candidate: 1.7.4-2
  Version table:
 *** 1.7.4-2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libpcap-dev:
[COLOR=#ff0000]  Installed: 1.7.4-2[/COLOR]
  Candidate: 1.7.4-2
  Version table:
 *** 1.7.4-2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status

```

---

