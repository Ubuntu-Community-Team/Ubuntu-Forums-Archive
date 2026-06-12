---
title: "Need help installing this file. xwii"
date: 2008-01-26
forum: General Help
---

### Post by onesojourner on 2008-01-26
I am trying to install xwii on my laptop. There is no install instructions though so I am not sure ho to go about it.

---

### Post by geraldm on 2008-01-26
It has a dependency for user-space libraries bluez-lib and bluez-utils, and it needs the kernel bluetooth stack.  The bluez-lib is in ubuntu.  bluez-utils is in debian, (I did not check ubuntu)
It also needs some X11 headers.
The package compiles OK. so it just needs a developer to package it.
If you are not intending to package it, then find the place to request that someone undertake that.  The programming work is done.  Just needs testing and packaging.

After installing dependencies, type make in the top directory of the source, and install it.


Gerald

---

### Post by onesojourner on 2008-01-26
I am willing to package it. I will need some one to walk me though it though.

---

### Post by onesojourner on 2008-01-27
I have added this to launchpad

[https://bugs.launchpad.net/getdeb.net/+bug/186376](https://bugs.launchpad.net/getdeb.net/+bug/186376)

---

