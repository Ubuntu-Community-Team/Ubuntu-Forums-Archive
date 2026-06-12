---
title: "Trouble compiling kernel deb on 14.04"
date: 2015-03-14
forum: General Help
---

### Post by Sotai on 2015-03-14
I seem to be hitting a similar problem as this bug report [https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/1308183](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/1308183)

I have installed the deb update on those comments, but now that I am trying to build kernel 3.18.x, even with the updated make-kpkg it's still happening.

```
/etc/kernel/postinst.d/apt-auto-removal: 84: /etc/kernel/postinst.d/apt-auto-removal: cannot create /etc/apt/apt.conf.d//01autoremove-kernels.dpkg-new: Permission denied
run-parts: /etc/kernel/postinst.d/apt-auto-removal exited with return code 2
make[3]: *** [install] Error 1
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/xxx/src/3.18.9'
make[1]: *** [debian/stamp/install/linux-image-3.18.9-ene] Error 2
make[1]: Leaving directory `/home/xxx/src/3.18.9'
make: *** [kernel-image] Error 2
```

Does someone know of a solution to this?

---

