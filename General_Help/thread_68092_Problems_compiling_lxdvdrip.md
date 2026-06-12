---
title: "Problems compiling lxdvdrip"
date: 2005-09-22
forum: General Help
---

### Post by Ibuntu_52 on 2005-09-22
ok I'm having a little problem getting lxdvdrip to compile.

this is what I do:

```
#tar -xvzf lxdvdrip
``` 

And it un-tars fine then I:

```
#cd /lxdvdrip
``` 

ok I', i'm in the /lxdvdrip directory so then I:

```
#./configure
``` 

and the terminal says:

```
bash: ./configure: No such file or directory
``` 

ok so I tried to make anyways.this is what happens:

```
gcc -g -ldvdread -lm -o lxdvdrip lxdvdrip.c
lxdvdrip.c:259:32: dvdread/dvd_reader.h: No such file or directory
lxdvdrip.c:260:30: dvdread/ifo_read.h: No such file or directory
lxdvdrip.c:261:31: dvdread/ifo_print.h: No such file or directory
In file included from lxdvdrip.c:283:
lxdvdrip.h:441: error: syntax error before '*' token
lxdvdrip.h:444: error: syntax error before '*' token
lxdvdrip.h:451: error: syntax error before '*' token
lxdvdrip.c:722: error: syntax error before '*' token
lxdvdrip.c: In function `dvdtime2msec':
lxdvdrip.c:724: error: `dt' undeclared (first use in this function)
lxdvdrip.c:724: error: (Each undeclared identifier is reported only once
lxdvdrip.c:724: error: for each function it appears in.)
lxdvdrip.c: At top level:
lxdvdrip.c:741: error: syntax error before '*' token
lxdvdrip.c: In function `millisekunden':
lxdvdrip.c:743: error: `dt' undeclared (first use in this function)
lxdvdrip.c: At top level:
lxdvdrip.c:861: error: syntax error before '*' token
lxdvdrip.c: In function `DVDGetFileSet':
lxdvdrip.c:892: error: `ifo_handle_t' undeclared (first use in this function)
lxdvdrip.c:892: error: `vmg_ifo' undeclared (first use in this function)
lxdvdrip.c:898: error: `_dvd' undeclared (first use in this function)
lxdvdrip.c: In function `main':
lxdvdrip.c:1298: error: `dvd_reader_t' undeclared (first use in this function)
lxdvdrip.c:1298: error: `dvd' undeclared (first use in this function)
lxdvdrip.c:1299: error: `ifo_handle_t' undeclared (first use in this function)
lxdvdrip.c:1299: error: `ifo_zero' undeclared (first use in this function)
lxdvdrip.c:1299: error: `ifo' undeclared (first use in this function)
lxdvdrip.c:1300: error: `pgcit_t' undeclared (first use in this function)
lxdvdrip.c:1300: error: `vts_pgcit' undeclared (first use in this function)
lxdvdrip.c:1301: error: `vtsi_mat_t' undeclared (first use in this function)
lxdvdrip.c:1301: error: `vtsi_mat' undeclared (first use in this function)
lxdvdrip.c:1302: error: `vmgi_mat_t' undeclared (first use in this function)
lxdvdrip.c:1302: error: `vmgi_mat' undeclared (first use in this function)
lxdvdrip.c:1303: error: `audio_attr_t' undeclared (first use in this function)
lxdvdrip.c:1303: error: `audio_attr' undeclared (first use in this function)
lxdvdrip.c:1304: error: `video_attr_t' undeclared (first use in this function)
lxdvdrip.c:1304: error: `video_attr' undeclared (first use in this function)
lxdvdrip.c:1305: error: `subp_attr_t' undeclared (first use in this function)
lxdvdrip.c:1305: error: `subp_attr' undeclared (first use in this function)
lxdvdrip.c:1306: error: `pgc_t' undeclared (first use in this function)
lxdvdrip.c:1306: error: `pgc' undeclared (first use in this function)
lxdvdrip.c:3128: error: syntax error before ')' token
make: *** [all] Error 1

``` 
 \\:-|/

does anyone know what I'm doing wrong?

---

