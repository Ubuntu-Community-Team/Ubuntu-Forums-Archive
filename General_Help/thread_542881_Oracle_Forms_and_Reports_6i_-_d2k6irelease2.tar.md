---
title: "Oracle Forms and Reports 6i - d2k6irelease2.tar"
date: 2007-09-04
forum: General Help
---

### Post by shivathreya on 2007-09-04
Has anyone installed Oracle Forms and Reports 6i on Feisty?

I tried and I am getting this error. I think it is related to libc6.

/home/oracle/orabase/app/oracle/product/6i/lib//libcore4.a(lnxpfl.o): In function `lnxpfl':
lnxpfl.c:(.text+0x129): undefined reference to `__ctype_tolower'
/home/oracle/orabase/app/oracle/product/6i/lib//libcore4.a(lsf3p.o): In function `lsf3pd':
lsf3p.c:(.text+0x1999): undefined reference to `__ctype_tolower'
lsf3p.c:(.text+0x1f9e): undefined reference to `__ctype_toupper'
lsf3p.c:(.text+0x21d4): undefined reference to `__ctype_toupper'
/home/oracle/orabase/app/oracle/product/6i/lib//libcore4.a(lsf3pc.o): In function `lsf3pcbg':
lsf3pc.c:(.text+0xa9): undefined reference to `__ctype_tolower'
lsf3pc.c:(.text+0x11a): undefined reference to `__ctype_tolower'
lsf3pc.c:(.text+0x3e0): undefined reference to `__ctype_toupper'
collect2: ld returned 1 exit status
make: *** [de60desm] Error 1


Please help!

Regards,

Shiva

---

### Post by suggsjc on 2007-10-26
I am having the exact same problem.  Has anyone else figured this out?  This is the very last remaining issue for me in being able to completely switch my work computer over to Ubuntu.

---

