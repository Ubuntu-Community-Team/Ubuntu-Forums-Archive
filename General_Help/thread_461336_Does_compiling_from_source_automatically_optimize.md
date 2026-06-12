---
title: "Does compiling from source automatically optimize?"
date: 2007-06-01
forum: General Help
---

### Post by juxtaposed on 2007-06-01
SImple question...

Does compiling from source automatically optimize for my processor? Or does it go with i386?

I use checkinstall to compile to deb files and then install them. Would that change anything?

---

### Post by yabbadabbadont on 2007-06-01
Just depends upon the options passed to gcc or g++ when the code was being compiled.  There would need to be either an "-march" or "-mcpu" option specifying your processor type before it would be optimized specifically for that CPU.

---

### Post by juxtaposed on 2007-06-01
How would I set that then? When I compile things I don't do anything with gcc or g++ directly, I just do the whole ./configure, make, checkinstall -D make install.

---

### Post by Rui Pais on 2007-06-01
> **juxtaposed said:**
> How would I set that then? When I compile things I don't do anything with gcc or g++ directly, I just do the whole ./configure, make, checkinstall -D make install.

i just added to my .bashrc:
```
CFLAGS="-march=<*your_arch_here*> -pipe"
CFLAGS="${CFLAGS} -O2"
CFLAGS="${CFLAGS} -fomit-frame-pointer"
#CFLAGS="${CFLAGS} *<another_options>*" 
#add any CFLAGS options as in the above lines...
export CFLAGS
export CXXFLAGS=${CFLAGS}
```
you can comment /uncomment each line of CFLAGS to add/remove more optimizations options...
Those are used by make. 
Checkinstall is just a script to do the deb will use the binaries made (and optimized by the make step.

---

### Post by yabbadabbadont on 2007-06-01
If you do that, then you probably should read through this:  [http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)

It has a lot of good information on which flags are safe to use with which processors.

---

### Post by Rui Pais on 2007-06-02
> **yabbadabbadont said:**
> If you do that, then you probably should read through this:  [http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)

It has a lot of good information on which flags are safe to use with which processors.

yes, excellent advice! 
thanks for the link yabbadabbadont.

My post was just to point how to set flags, not what flag to use... so i use mine as examples. Not a good idea (people may blibly copy+paste). I edit to be more abstract.

---

