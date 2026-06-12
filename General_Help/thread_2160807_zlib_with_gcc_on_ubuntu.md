---
title: "zlib with gcc on ubuntu"
date: 2013-07-08
forum: General Help
---

### Post by priyaanand on 2013-07-08
Hi
I want to use zlib "inf" and "def" functions.
I use the following command for compiling

"gcc practice.m practicemain.m `gnustep-config --objc-flags` -lobjc -lgnustep-base -o practicemain"

and I get the following error

"In function ‘-[practiceClass meth]’:
practice.m:12:2: warning: implicit declaration of function ‘inf’ [-Wimplicit-function-declaration]
practice.m:8:11: warning: unused variable ‘strm’ [-Wunused-variable]
practice.m:12: error: undefined reference to 'inf'
collect2: ld returned 1 exit status"

kindly help
TIA

---

### Post by Impavidus on 2013-07-08
I can't really find the inf() and def() functions in the [manual]("http://www.zlib.net/manual.html"). Are you sure it shouldn't be inflate() and deflate()?

---

### Post by priyaanand on 2013-07-08
Hi
I have installed zlib 1.2.3 on my ubuntu machine.Can you please suggest me a clear example as in how to use zlib in my code?I wantr to compress and decompress xlsx files.

TIA

---

### Post by priyaanand on 2013-07-09
Hi
I have installed zlib 1.2.3 on my ubuntu machine.Can you please suggest  me a clear example as in how to use zlib in my code?I wantr to compress  and decompress xlsx files.

TIA

When i try compiling zpipe.c with gcc zpipe.c -o zpipe
i get the following errors


/tmp/ccmPtJaa.o:zpipeOrg.c:function def: error: undefined reference to 'deflateInit_'
/tmp/ccmPtJaa.o:zpipeOrg.c:function def: error: undefined reference to 'deflateEnd'
/tmp/ccmPtJaa.o:zpipeOrg.c:function def: error: undefined reference to 'deflate'
/tmp/ccmPtJaa.o:zpipeOrg.c:function def: error: undefined reference to 'deflateEnd'
/tmp/ccmPtJaa.o:zpipeOrg.c:function def: error: undefined reference to 'deflateEnd'
/tmp/ccmPtJaa.o:zpipeOrg.c:function inf: error: undefined reference to 'inflateInit_'
/tmp/ccmPtJaa.o:zpipeOrg.c:function inf: error: undefined reference to 'inflateEnd'
/tmp/ccmPtJaa.o:zpipeOrg.c:function inf: error: undefined reference to 'inflate'
/tmp/ccmPtJaa.o:zpipeOrg.c:function inf: error: undefined reference to 'inflateEnd'
/tmp/ccmPtJaa.o:zpipeOrg.c:function inf: error: undefined reference to 'inflateEnd'
/tmp/ccmPtJaa.o:zpipeOrg.c:function inf: error: undefined reference to 'inflateEnd'
collect2: ld returned 1 exit status

here zpipeOrg.c is nothing but zpipe.c

TIA

---

### Post by priyaanand on 2013-07-09
I solved it by linking the code to zlib with:

gcc  zlib.c -o zlib -lz

It compiles.
My question is, after .exe is generated when I type  "./zpipe"
Nothing is displayed.What is the expected output?

TIA

---

