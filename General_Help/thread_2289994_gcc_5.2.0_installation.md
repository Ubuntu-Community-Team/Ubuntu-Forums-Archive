---
title: "gcc 5.2.0 installation"
date: 2015-08-08
forum: General Help
---

### Post by Abu_Hurayrah on 2015-08-08
Hello there!! I'm trying to install the gcc 5.2.0 on my ubuntu 14.04, but I don't know how? I have downloaded it from one of the mirror sites provided, but now what do I do with this .tar.gz file? I don't even know how to compile drivers. Please help.

---

### Post by bithunter2 on 2015-08-12
Hello,

to get a useful toolchain you would need to download more source packages than just gcc 5.2.0 itself. E.g. binutils, mpfr, gmp, mpc, isl (0.14 [release 5.2.0 won't compile with 0.15 out of the box]), the kernel(headers), glibc. This is almost the same for building cross toolchains. You would also need to know the configure options of your target system for each package and the correct order. For a fresh Ubuntu install you probably need to also install build-essential, lzip, texinfo and more. So in short compiling a toolchain is a somewhat involved process. Also note, that 5.2.0 is very new (16 July 2015). If you need a recent toolchain, you could try to add this ppa: [https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/ppa) and install via apt.

---

### Post by monkeybrain20122 on 2015-08-12
[http://www.linuxfromscratch.org/lfs/view/development/chapter06/gcc.html](http://www.linuxfromscratch.org/lfs/view/development/chapter06/gcc.html)

Check the paths carefully, make sure you don't overwrite the system's gcc. To be safe you can just install it in $HOME and set environmental variables whenever you want to use it instead of system gcc. But believe me building gcc from scratch is a pain.

P.S. If you don't even know what to do with the tar.gz file why do you want a different gcc?? (older versions of gcc are sometimes needed for compatible reasons e.g Matlab, but installing an older version and switching between it and the default are quite easy in Debian based systems. I doubt that anything would require gcc 5.2.0)

---

