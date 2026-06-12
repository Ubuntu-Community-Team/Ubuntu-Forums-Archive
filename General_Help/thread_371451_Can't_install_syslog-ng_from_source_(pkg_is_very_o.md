---
title: "Can't install syslog-ng from source (pkg is very old)"
date: 2007-02-26
forum: General Help
---

### Post by jimmythegeek on 2007-02-26
I want to set up syslog-ng on a Dapper host, but the available package is 1.6 and the current (source) release is 2.02

When I download the tarball and extract it, then try to ./configure, I get an error "checking for GLIB... configure: error: Cannot find GLib library version >= 2.2: is pkg-config in path?"

pkg-config IS in the path.  

It looks like GLIB is libc6.  

sudo  apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I can't actually determine what the FILE NAME of the library being sought is, so I don't have much hope of figuring out what value to pass, even if I knew what parameter configure was looking for.  

Anybody else been down this road?

---

### Post by llamakc on 2007-02-26
When you are compiling software on Debian-based systems and the configure errors out on a package name, try searching for and installing the PACKAGENAME-dev package. This should fix your issue.

---

