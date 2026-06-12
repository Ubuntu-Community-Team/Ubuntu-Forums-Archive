---
title: "dpkg error after installation of anything."
date: 2007-08-12
forum: General Help
---

### Post by daverich on 2007-08-12
E: runit: subprocess post-installation script returned error exit status 1

is what i get after installing/uninstalling anything.

the details say that -

Errors were encountered while processing:
 runinit
E:Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up runit (1.6.0-1) ...
grep /etc/inittab: No such file or directory
grep /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat '/etc/inittab/: No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1


and why on earth can you not cut/paste from it heh ;) 

any ideas?

The app does install/uninstall but this error is annoying.

Kind regards

Dave Rich

---

### Post by madjid on 2007-08-15
Hi there,

I was getting the same error but I found the solution on ubuntu launchpad:

[https://bugs.launchpad.net/ubuntu/+source/runit/+bug/117880]("https://bugs.launchpad.net/ubuntu/+source/runit/+bug/117880")

:)

Madjid

---

### Post by daverich on 2007-08-15
thanks!

Kind regards

Dave Rich

---

