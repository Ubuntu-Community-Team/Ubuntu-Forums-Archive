---
title: "build uClibc in Linaro Ubuntu ARM"
date: 2014-05-16
forum: General Help
---

### Post by kay_niv on 2014-05-16
I'm not able to run a executable in ubuntu on Udoo H/W , after "readelf" ing the executable command, I got "[Requesting program interpreter: /lib/ld-uClibc.so.0]" .. 
So i checked the installation or library in my linux and was not able to find it.

so to get tot "/lib/ld-uClibc.so.0" , I decided to build the uClibc from the sources :( , I got
  CC ldso/ldso/ldso.oS
In file included from ./ldso/include/ldso.h:36,
                 from ldso/ldso/ldso.c:33:
./ldso/include/dl-syscall.h: In function `_dl_open':
./ldso/include/dl-syscall.h:69: error: `__NR_open' undeclared (first use 
in this function)
......

what should i do ?(apart from ](*,)](*,)](*,)](*,)[FONT=Verdana])[/FONT]

---

