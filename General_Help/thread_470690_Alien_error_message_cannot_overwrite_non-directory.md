---
title: "Alien error message: cannot overwrite non-directory"
date: 2007-06-11
forum: General Help
---

### Post by woland on 2007-06-11
Hello folks!

I'm trying to install an rpm package. I'm using alien to conver the rpms to debs, however 2 two packages that Ive tried alien had exited woth an error message:
```

woland@woland-laptop:~/picotux$ sudo alien cpp-4.1-arm-linux-gnu-4.1.1-22.i386.rpm 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/cpp-4.1-arm-linux-gnu
cp: cannot overwrite directory `debian/cpp-4.1-arm-linux-gnu/usr/share/doc/cpp-4.1-arm-linux-gnu' with non-directory
make: *** [binary-arch] Error 123
find: cpp-4.1-arm-linux-gnu-4.1.1: No such file or directory
```

Any ideas on how to solve it?

---

