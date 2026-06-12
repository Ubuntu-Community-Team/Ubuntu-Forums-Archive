---
title: "can't compile gutenprint-5.1.7"
date: 2008-05-03
forum: General Help
---

### Post by ptero on 2008-05-03
i can't compile new gutenprint drivers (which should work with epson stylus dx4450, which i can't get to work with other drivers).
i get following error message:
```
genppd.c:81:25: error: cups/raster.h: No such file or directory
genppd.c: In function ‘write_ppd’:
genppd.c:1346: error: ‘CUPS_CSPACE_W’ undeclared (first use in this function)
genppd.c:1346: error: (Each undeclared identifier is reported only once
genppd.c:1346: error: for each function it appears in.)
genppd.c:1346: error: ‘CUPS_ORDER_CHUNKED’ undeclared (first use in this function)
genppd.c:1353: error: ‘CUPS_CSPACE_K’ undeclared (first use in this function)
genppd.c:1363: error: ‘CUPS_CSPACE_RGB’ undeclared (first use in this function)
genppd.c:1370: error: ‘CUPS_CSPACE_CMY’ undeclared (first use in this function)
genppd.c:1377: error: ‘CUPS_CSPACE_CMYK’ undeclared (first use in this function)
genppd.c:1384: error: ‘CUPS_CSPACE_KCMY’ undeclared (first use in this function)
make[3]: *** [gutenprint_5_1-genppd.o] Error 1
make[3]: Leaving directory `/home/ku/download/gutenprint-5.1.7/src/cups'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ku/download/gutenprint-5.1.7/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ku/download/gutenprint-5.1.7'
make: *** [all] Error 2

```
the same message appears when i try to compile 5.1.98.2.

---

### Post by _sluimers_ on 2008-06-04
I have the same problem, did you figure out how to fix this?

---

