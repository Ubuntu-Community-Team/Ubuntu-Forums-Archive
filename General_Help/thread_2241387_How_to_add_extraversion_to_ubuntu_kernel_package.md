---
title: "How to add extraversion to ubuntu kernel package"
date: 2014-08-25
forum: General Help
---

### Post by Douglas_Lehr on 2014-08-25
Hi All,
  I created a post regarding the make-kpkg tool giving errors.  With that being an issue, I tried to patch, build, and package a new kernel using the steps described here
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
What I can't find for the life of me, is where we can add our own version to the end of the kernel name.  I've tried modifying some files within the debian/rules.d directory to see if I can slide in something after the "linux-image-3.16.0-9-generic_" naming, but I can't seem to find how.  Would anyone know how, using the link above, I can go about adding a custom version to my build?  I'm on a power8 box and am willing to try out various suggestions if folks have them.  Thanks for your time!

---

### Post by Doug S on 2014-08-26
Instead of, and for example:```
 make -j8 deb-pkg
```do this:```
make -j8 deb-pkg LOCALVERSION=-doug2
```

---

