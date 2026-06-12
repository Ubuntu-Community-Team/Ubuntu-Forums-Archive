---
title: "Cannot install emacs-common"
date: 2024-10-21
forum: General Help
---

### Post by Acharn on 2024-10-21
I've been having lots of trouble trying to install emacs lately. I finally got emacs installed using snap (which I do not like), but it needs emacs-common. When I try to install emacs-common with 'sudo apt install emacs-common' it fails and recommends I try 'sudo apt --fix-broken install' without a package name. That gives me:
```

Unpacking emacs-common (1:29.3+1-1ubuntu2+esm1) ...
dpkg: error processing archive /var/cache/apt/archives/emacs-common_1%3a29.3+1-1
ubuntu2+esm1_all.deb (--unpack):
 trying to overwrite '/usr/include/emacs-module.h', which is also in package ema
cs28 28.1~1.git5a223c7f2e-kk3+22.04
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/emacs-common_1%3a29.3+1-1ubuntu2+esm1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't know what to do next. Should I submit a bug report? Is there a maintainer I should contact? What should I do?

ubuntu-bug says this problem cannot be reported because the package is not installed.

---

