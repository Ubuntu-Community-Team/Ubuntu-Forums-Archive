---
title: "apt-source woes"
date: 2005-10-04
forum: General Help
---

### Post by toran on 2005-10-04
Hi guys, I've just recently installed a program using the apt-get source method (apt-get source <package>; apt-get source -b <package>)

Unfortunately, whenever I run "apt-get upgrade", it wants to revert this package from my custom-built version to the global repository version. How can I keep it from doing this?

Thanks!

---

### Post by mlomker on 2005-10-04
> Unfortunately, whenever I run "apt-get upgrade", it wants to revert this package from my custom-built version to the global repository version. How can I keep it from doing this?

When you use Synaptic you can 'lock' the package but things are more complicated from the command line.  The only option that I can think of would be to create a local repository and then using [apt-pinning]("http://wiki.debian.net/index.cgi?AptPinning") to give it a higher priority.

I've never actually done it, so I can't provide specific help with it.

---

