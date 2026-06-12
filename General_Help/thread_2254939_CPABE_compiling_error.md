---
title: "CPABE compiling error"
date: 2014-12-01
forum: General Help
---

### Post by ZakkWylde on 2014-12-01
Hi I need to run some tests with a CP ABE toolkit I've found [http://acsc.cs.utexas.edu/cpabe/](http://acsc.cs.utexas.edu/cpabe/), I'm a total newbie of Linux, I've started using for a few days, so please bear with me.  
 I've found this video tutorial [https://www.youtube.com/watch?v=aXDQ1J8kRw0](https://www.youtube.com/watch?v=aXDQ1J8kRw0) that was quite helpful which made me install:
 -m4 macro processing language
 -gmp library
 -pbc library
 -libcrypt
 -libssl
 -libglib2.0
 -libbswabe library  
 
 
 I've followed every single passage of the video, but when I have to compile the cpabe package after the make this error pops up (while it doesn't seem the case in the tutorial)
 
 
 ```
~/Downloads/cpabe-0.11$ make
 gcc -c -o setup.o setup.c -O3 -Wall -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pbc -I/usr/local/include/pbc -DPACKAGE_NAME=\"cpabe\" -DPACKAGE_TARNAME=\"cpabe\" -DPACKAGE_VERSION=\"0.11\" -DPACKAGE_STRING=\"cpabe\ 0.11\" -DPACKAGE_BUGREPORT=\"bethenco@cs.berkeley.edu\" -DPACKAGE_URL=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSTDC_HEADERS=1 -DHAVE_FCNTL_H=1 -DHAVE_STDDEF_H=1 -DHAVE_STRING_H=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_VPRINTF=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBCRYPTO=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_MEMSET=1 -DHAVE_GMP=1 -DHAVE_PBC=1 -DHAVE_BSWABE=1
 gcc -c -o common.o common.c -O3 -Wall -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pbc -I/usr/local/include/pbc -DPACKAGE_NAME=\"cpabe\" -DPACKAGE_TARNAME=\"cpabe\" -DPACKAGE_VERSION=\"0.11\" -DPACKAGE_STRING=\"cpabe\ 0.11\" -DPACKAGE_BUGREPORT=\"bethenco@cs.berkeley.edu\" -DPACKAGE_URL=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSTDC_HEADERS=1 -DHAVE_FCNTL_H=1 -DHAVE_STDDEF_H=1 -DHAVE_STRING_H=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_VPRINTF=1 -DHAVE_LIBCRYPTO=1 -DHAVE_LIBCRYPTO=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_MEMSET=1 -DHAVE_GMP=1 -DHAVE_PBC=1 -DHAVE_BSWABE=1
 common.c: In function ‘suck_file’:
 common.c:137:2: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
   fread(a->data, 1, s.st_size, f);
   ^
 common.c: In function ‘read_cpabe_file’:
 common.c:211:2: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
   fread((*aes_buf)->data, 1, len, f);
   ^
 common.c:218:2: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
   fread((*cph_buf)->data, 1, len, f);
   ^
 gcc -o cpabe-setup setup.o common.o -O3 -Wall -lglib-2.0 -Wl,-rpath /usr/local/lib -lgmp -Wl,-rpath /usr/local/lib -lpbc -lbswabe -lcrypto -lcrypto  
 [B]<b>/usr/bin/ld: /usr/local/lib/libpbc.so: undefined reference to symbol '__gmpz_init'
 /usr/local/lib/libgmp.so: error adding symbols: DSO missing from command line
 collect2: error: ld returned 1 exit status
 Makefile:34: recipe for target 'cpabe-setup' failed</b>
 make: *** [cpabe-setup] Error 1</pre></code[/B]
```
 
 Thanks

---

### Post by ZakkWylde on 2014-12-01
Anyone?

---

### Post by sonia5 on 2015-02-03
I m also facing same problem ...m using ubuntu desktop 14.04  ....please suggest solution

---

### Post by Holger_Gehrke on 2015-02-03
Found by googling: ubuntu undefined reference to symbol '__gmpz_init'

[http://stackoverflow.com/questions/17373306/error-in-linking-gmp-while-compiling-cpabe-package-from-its-source-code](http://stackoverflow.com/questions/17373306/error-in-linking-gmp-while-compiling-cpabe-package-from-its-source-code)

---

