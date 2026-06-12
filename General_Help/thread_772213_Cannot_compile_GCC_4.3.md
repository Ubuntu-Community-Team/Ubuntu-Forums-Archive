---
title: "Cannot compile GCC 4.3"
date: 2008-04-28
forum: General Help
---

### Post by singler on 2008-04-28
I tried to compile GCC 4.3 (from SVN) on a Sun T5120 (Niagara 2). 
However, there is a problem with this MPFR library. Also installed, there are error messages like that.

/usr/bin/ld: skipping incompatible /home/singler/install/mpfr/lib/libmpfr.so when searching for -lmpfr
/usr/bin/ld: skipping incompatible /home/singler/install/mpfr/lib/libmpfr.a when searching for -lmpfr
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libmpfr.so when searching for -lmpfr
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libmpfr.a when searching for -lmpfr
/usr/bin/ld: skipping incompatible /usr/lib/libmpfr.so when searching for -lmpfr
/usr/bin/ld: skipping incompatible /usr/lib/libmpfr.a when searching for -lmpfr
/usr/bin/ld: cannot find -lmpfr

Does anybody know how to fix this problem? Why is the library "incompatible"? I compiled it from source on the same machine.

In configured GCC in an object diretory using

../branch_1/configure --enable-languages=c,c++ --program-suffix=-rep --prefix=/home/singler/gcc/install_branch_1 --with-mpfr=/home/singler/install/mpfr

All the compilation runs fine.

-- Johannes

---

### Post by singler on 2008-05-02
I have successfully upgraded to 8.04, but the problem remains.

Also, I'm pretty sure that the problem is not specific for GCC compilation, but more general, concerning the ABI on sparc. Does anybody have an idea?

---

### Post by Kirfew on 2008-05-02
Just install MPFR from the APT package manager
sudo apt-get install libgmp3-dev libmpfi-dev libmpfr1ldbl libmpfr-dev

---

### Post by singler on 2008-05-02
Thanks for the hint, but it does not fix the problem completely. The configure script now takes the MPFR installed in the system, not my self-compiled one. That looks better than before. However, the build process (after complete cleanup) fails with about the same error messages:

/usr/bin/ld: skipping incompatible /usr/bin/../lib/libmpfr.so when searching for -lmpfr
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libmpfr.a when searching for -lmpfr
/usr/bin/ld: skipping incompatible /usr/lib/libmpfr.so when searching for -lmpfr
/usr/bin/ld: skipping incompatible /usr/lib/libmpfr.a when searching for -lmpfr

---

### Post by singler on 2008-05-16
Finally, I got it compiled by adding 

--disable-multilib --host=sparc-unknown-linux-gnu --target=sparc-unknown-linux-gnu --build=sparc-unknown-linux-gnu

to the configure command. But I'm not sure whether I have the right thing now.

---

