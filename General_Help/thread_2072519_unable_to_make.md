---
title: "unable to make"
date: 2012-10-18
forum: General Help
---

### Post by buffchick on 2012-10-18
Something is missing and I can't figure out what. I'm chrooted into a debootstrap image and I'm trying to update the NIC drivers.
```
root@svr:/temp/Linux/Driver/netxtreme2-7.2.20# make
make -C bnx2/src  KVER=2.6.32-38-server PREFIX=
make[1]: Entering directory `/temp/Linux/Driver/netxtreme2-7.2.20/bnx2-2.72.13/src'
make -C  SUBDIRS=/temp/Linux/Driver/netxtreme2-7.2.20/bnx2-2.72.13/src modules
make: Entering an unknown directory
make: *** SUBDIRS=/temp/Linux/Driver/netxtreme2-7.2.20/bnx2-2.72.13/src: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [default] Error 2
make[1]: Leaving directory `/temp/Linux/Driver/netxtreme2-7.2.20/bnx2-2.72.13/src'
make: *** [l2build] Error 2
root@svr:/temp/Linux/Driver/netxtreme2-7.2.20#

```

---

### Post by shreepads on 2012-10-18
What do you get from

$ ls -al /temp/Linux/Driver/netxtreme2-7.2.20

and

$ ls -al /temp/Linux/Driver/netxtreme2-7.2.20/bnx2-2.72.13

---

