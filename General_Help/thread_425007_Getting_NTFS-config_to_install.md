---
title: "Getting NTFS-config to install?"
date: 2007-04-27
forum: General Help
---

### Post by Brandnew70x7 on 2007-04-27
Hey guys been tyring for like an hour to find a solution to this.. anyone know?

> ryan@ryan-desktop:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ntfs-config: Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
               Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
               Depends: libcairo2 (>= 1.2.4) but 1.0.4-0ubuntu1 is to be installed
               Depends: libdbus-1-3 but it is not installable
               Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
               Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
               Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be installed
               Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed
               Depends: ntfs-3g but it is not going to be installed
E: Broken packages

Any help is appreciated thanks in advance :)

---

### Post by lw5 on 2007-04-27
Did you do an 'sudo apt-get update' before trying this? You should have.
Otherwise, apt should have given you the suggestion of running apt-get with the -f option (also see man apt-get). Try that.

---

### Post by Brandnew70x7 on 2007-04-27
I'll give it a try. :>

---

### Post by Brandnew70x7 on 2007-04-27
Still the same error! Fresh install too :( Whats going on

---

