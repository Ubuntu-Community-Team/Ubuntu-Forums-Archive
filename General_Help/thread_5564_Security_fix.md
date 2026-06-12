---
title: "Security fix"
date: 2004-11-19
forum: General Help
---

### Post by Klunk on 2004-11-19
I have just installed the security fix as detailed in this post ([http://www.ubuntuforums.org/showthread.php?t=5463](http://www.ubuntuforums.org/showthread.php?t=5463)).

How can I tell if it has actually updated teh kernel as a uname -a still shows the same kernel vrion. I think it might have worked because I think the date has changed but how can I be sure ?

---

### Post by az on 2004-11-19
Good question!

You will have the same version number kernel, it is the kernel-image package number that will be higher.  Look in synaptic at the kernel-image you have installed.  Right-click and check the propertied.  You will see that it comes from the security repository and not the main.  You should also see the date if I am not mistaken...

The packages in a stable release will usually not change, just get patched.  You end up with the same version of the package, just with security patches.

---

### Post by jdong on 2004-11-19
Yeah, kernel version stays the same, the kernel package's revision has been increased.
 
 ```

 jdong@jd64:~ $ dpkg --status linux-k7
 Package: linux-k7
 Status: install ok installed
 Priority: optional
 Section: restricted/base
 Installed-Size: 48
 Maintainer: Herbert Xu <herbert@gondor.apana.org.au>
 Architecture: i386
 Source: linux-meta
 Version: 2.6.8.1-14
 Depends: linux-image-k7, linux-restricted-modules-k7
 Description: Complete Linux kernel on AMD K7.
  This package will always depend on the latest complete Linux kernel available
  for AMD Duron/Athlon.
 
 
```

---

