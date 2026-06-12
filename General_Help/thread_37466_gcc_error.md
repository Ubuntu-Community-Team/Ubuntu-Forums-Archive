---
title: "gcc error"
date: 2005-05-27
forum: General Help
---

### Post by wasynyt on 2005-05-27
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

in config.log

configure:1753: checking for C compiler default output file name
configure:1756: gcc    conftest.c  >&5
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: File fo
collect2: ld returned 1 exit status
configure:1759: $? = 1
configure: failed program was:
| /* confdefs.h.  */

and

/usr/lib/gcc-lib/i486-linux/3.3.5$ dir
cc1       crtbegin.o   crtend.o   include      libgcc_s.so   libsupc++.a
cc1plus   crtbeginS.o  crtendS.o  libgcc.a     libstdc++.a   specs
collect2  crtbeginT.o[COLOR=Blue]  crt1.o     [/COLOR]libgcc_eh.a  libstdc++.so

im totally confused
so any help is welcome

---

### Post by enric on 2005-05-27
I'm having exactly the same problem.  This happens after dist-upgrading the last version of binutils (the linker is broken).

I hope it will be fixed real soon.  By now, **gcc is completely unusable**.

Does anybody know how to downgrade to the previous version of binutils (or somehow fix this problem)?

---

### Post by enric on 2005-05-27
Here's how to reproduce this problem:

```

 $ echo 'int main(){return 0;}' > /tmp/z.c ; gcc /tmp/z.c
 /usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o: file not recognized: File format not recognized
 collect2: ld returned 1 exit status

```

---

### Post by jsemczyk on 2005-05-27
You can use **aptitude** to downgrade, it makes it very easy and then you have a working ld.

JoN

---

### Post by rum beverage on 2005-05-27
and how do you go about doing this?

---

### Post by wasynyt on 2005-05-28
i have a fresh install of hoary 5.04... aye no upgrade so i dont want to downgrade i just want it to work

---

### Post by wasynyt on 2005-05-28
found help from another post 
[http://ubuntuforums.org/showthread.php?t=37516&highlight=gcc](http://ubuntuforums.org/showthread.php?t=37516&highlight=gcc)

hope it will help

---

### Post by lorap on 2005-05-30
hi friend!
try "cc" native unix c compiler.
it's one i like mostly.
working with it many years with no trouble.
pavel

---

### Post by wasynyt on 2005-05-30
i have no mine compiler working thanks to that updater so i have no further intres in this area.. but if someone needs help im ready to try and search for adittional information conserning this subject

---

### Post by lorap on 2005-05-30
hi!
it's just impossible.
cc comes built in.

---

### Post by wasynyt on 2005-05-30
i would actually want to know what is?
so what if its build in... it can still be broken

---

