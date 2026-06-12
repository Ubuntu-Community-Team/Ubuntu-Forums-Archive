---
title: "xorg server confusion"
date: 2013-04-09
forum: General Help
---

### Post by D0natell0 on 2013-04-09
I'm trying to build an Intel linux graphics driver and getting an error about an invalid package.

Kernel: 2.6.24-32-generic
Intel 2010Q4 (from [www.01.org/linuxgraphics]("http://www.01.org/linuxgraphics") designed for kernel 2.6.37, the oldest they provide)

When I run ./configure I get the error: 
```
Requested 'xorg-server >= 1.6' but version of xorg-server is 1.4.0.90
```

However, Synaptic says I've got v1.7, as does this:
```
sudo apt-cache show xutils-dev
Version: 1:7.2.ds2-1ubuntu1

```

Also, the abbreviated contents of "/usr/lib/pkgconfig/xorg-server.pc" are:
```
Name: xorg-server
Description: Modular X.Org X Server
Version: 1.4.0.90
```

So, I think my question is how do I get this driver to install? Why the discrepancy between these definitions of x server?
Thanks in advance.

---

