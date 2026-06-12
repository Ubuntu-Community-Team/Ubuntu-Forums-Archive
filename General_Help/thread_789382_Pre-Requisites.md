---
title: "Pre-Requisites"
date: 2008-05-10
forum: General Help
---

### Post by yoggi on 2008-05-10
I Need these in order to kompile sasc-ng:

/lib/modules/`uname -r`/build
/lib/modules/`uname -r`/source

As Pre-Requisites

I require the source for the kernel (not just the kernel-headers) installed and linked correctly.

How do I install and link the kernel-source properly?

Help would be appreciated 

Yoggi

---

### Post by Monicker on 2008-05-10
From a terminal:

```
apt-cache search linux-source
```

---

### Post by yoggi on 2008-05-10
Sorry but I can't see how dose this help me.

---

### Post by Monicker on 2008-05-10
You said you need the kernel source.  That is what the linux-source package contains.  It clearly states that in the description when it shows up in the search results.

---

### Post by yoggi on 2008-05-10
Yes but how do I make the link (softlink I think) so that 

/lib/modules/`uname -r`/build
/lib/modules/`uname -r`/source

are linked correctly?

These are the instructions Ill am trying to follow.
[https://opensvn.csie.org/traccgi/sascng/wiki/SascInstall](https://opensvn.csie.org/traccgi/sascng/wiki/SascInstall)

---

