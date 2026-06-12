---
title: "[Kernel PPA] linux-update-symlinks not available in all Ubuntu versions"
date: 2018-04-27
forum: General Help
---

### Post by Menion on 2018-04-27
Hi all
This is not a request of support for the mainline kernel from PPA, but I report that starting from kernel v4.16.4 the image package now requires linux-update-symlinks in postinst script, which is not available in all Ubuntu version, in Xenial for sure
This perl script is part of linux-base package, available in Debian.
A workaround is to install such package from debian, but with possible package conflicts side-effects
If you know a better place to report this, please let me know
Bye

---

### Post by deadflowr on 2018-04-27
> If you know a better place to report this, please let me know
Report it to Launchpad,
or ask the kernel team on their mailing list.

[https://launchpad.net/~ubuntu-kernel-team]("https://launchpad.net/~ubuntu-kernel-team")
[https://lists.ubuntu.com/mailman/listinfo/kernel-team]("https://lists.ubuntu.com/mailman/listinfo/kernel-team")

---

