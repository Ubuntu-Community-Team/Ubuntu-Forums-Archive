---
title: "emacs22-common and emacs22-common-non-dfsg conflict on a file's ownership"
date: 2008-04-03
forum: General Help
---

### Post by vpit3833 on 2008-04-03
On my eeepc 4G, I use Xubuntu(gutsy) and I want to install the emacs info pages.  So I do 'sudo apt-get install emacs22-common-non-dfsg'.

I get the following in return instead.
..
Unpacking emacs22-common-non-dfsg (from .../emacs22-common-non-dfsg_22.1+1-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/emacs22-common-non-dfsg_22.1+1-1_all.deb (--unpack):
 trying to overwrite `/usr/share/emacs/22.1/etc/CENSORSHIP', which is also in package emacs22-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/emacs22-common-non-dfsg_22.1+1-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

emacs22-common was installed automatically while intalling emacs22.

Is there some other way to install emacs info pages Xubuntu way?

---

