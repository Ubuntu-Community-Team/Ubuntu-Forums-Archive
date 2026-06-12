---
title: "How do I know what type of distribution a computer is?"
date: 2004-11-02
forum: General Help
---

### Post by xutopia on 2004-11-02
I ssh back and forth between all kinds of machine at work.  Some are Ubuntu, some are redhat. slackware or Gentoo.   Is there a way to know what distribution a machine runs?  I don't even know how to in the console if a machine is running Ubuntu!

---

### Post by jdong on 2004-11-02
If /etc/sysconfig exists, it's a dead-sure sign of a Redhat-derivative (Fedora, Mandrake) distro.

Debian will have an /etc/debian_version file.

Look for apt (debian), yast (suse), rpm, urpmi (mandrake's 'apt'), and such distribution-specific files.

---

### Post by Cygnia on 2004-11-02
More often than not the contents of /proc/version will clearly indicate the distro that compiled that system; for example in my case:

Linux version 2.6.8.1-3-amd64-generic (buildd@crested) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Oct 12 11:40:38 UTC 2004

Unless the machine has a custom kernel, iin which case you could get philosophical and say they're essentially using their own distro in effect.

---

### Post by jdong on 2004-11-02
along that line, **gcc -v** would work, too!

---

### Post by macsaint on 2004-11-02
Hm... You can use

uname -a

it will show the information..

---

### Post by Cygnia on 2004-11-02
It doesn't show the distro though, mine results in:

cygnia@cygniapolis:~ $ uname -a
Linux cygniapolis 2.6.8.1-3-amd64-generic #1 Tue Oct 12 11:40:38 UTC 2004 x86_64 GNU/Linux

---

### Post by HungSquirrel on 2004-11-02
Many distros put information about the distro in /etc/issue, /etc/motd, and similar places.  For example, on an Ubuntu system, /etc/issue is:
```
Ubuntu 4.10 "Warty Warthog" \n \l
```

There are many dead givaways for Redhat systems...such as /etc/redhat-version. ;)

---

