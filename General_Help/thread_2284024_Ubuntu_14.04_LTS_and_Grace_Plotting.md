---
title: "Ubuntu 14.04 LTS and Grace Plotting"
date: 2015-06-26
forum: General Help
---

### Post by patrickdeanmullen on 2015-06-26
Dear all, 

I recently installed Ubuntu 14.04.2 LTS on a new Dell Inspiron 7000 series (model 7458) and downloaded Grace from the Ubuntu Software Center.  See version below: 

Grace-5.1.23

GUI toolkit: @(#)Motif Version 2.3.4
Xbae version: 46004
T1lib: 1.3.1p3-grace
FFT: FFTW
NetCDF support: on
libpng: 1.2.50
libjpeg: 80
Built: Wed Apr  9 16:10:05 2014 on Linux #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 3.2.0-58-generic x86_64
Compiler flags: gcc -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -I.. -I. -I../T1lib/t1lib  -D_FORTIFY_SOURCE=2  -Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -Wl,--as-needed -lXmHTML -lXbae -lXm -lXpm -lXmu -lXt -lXext -lX11  -lSM -lICE  ../cephes/libcephes.a -lnetcdf -lfftw3 ../T1lib/libt1.a  -ljpeg -lpng -lz -ldl -lm  

Registered devices:
X11 PostScript EPS MIF SVG PNM JPEG PNG Metafile 

(C) Copyright 1991-1995 Paul J Turner
(C) Copyright 1996-2012 Grace Development Team
All Rights Reserved

When attempting to open some *.agr files created on another machine, grace crashes/ screen goes black/ I must log back in.  If I successfully open the grace file, I again see grace crashing when I select File --> Print SetUp --> EPS --> Apply.  Some files work perfectly fine.  I do not have any problems with Grace files that are made on my local machine.  Files that are crashing the program are generated from xmgrace installed on Mac OS Yosemite using xQuartz.  Does anyone know what the source of the crashing is? I require this program for my work so any help would be greatly appreciated! 

Best, 
Patrick

---

### Post by steveo314 on 2015-06-26
Is your version of Grace on your Mac way newer than the Trusty version?

---

### Post by patrickdeanmullen on 2015-06-26
Thanks for the response steveo! Here is the Mac xmgrace version info:

Grace-5.1.23


GUI toolkit: @(#)GNU/LessTif Version 2.1 Release 0.95.2
Xbae version: 4007
T1lib: 1.3.1p3-grace
FFT: built-in
NetCDF support: off
libpng: 1.6.12
libjpeg: 80
PDFlib: 7.0.5p3
Built: Wed Sep 24 23:14:14 2014 on Darwin Darwin Kernel Version 13.4.0: Sun Aug 17 19:50:11 PDT 2014; root:xnu-2422.115.4~1/RELEASE_X86_64 13.4.0 x86_64
Compiler flags: clang -O2  -fno-common -Wall -Wpointer-arith -Wnested-externs -I.. -I. -I../T1lib/t1lib -I../Xbae    ../Xbae/Xbae/libXbae.a -lXm -lXpm -lXp -lXmu -lXt -lXext -lX11  -lSM -lICE  ../cephes/libcephes.a   ../T1lib/libt1.a -lpdf -ljpeg -lpng -lz -lm  


Registered devices:
X11 PostScript EPS PDF MIF SVG PNM JPEG PNG Metafile 


(C) Copyright 1991-1995 Paul J Turner
(C) Copyright 1996-2012 Grace Development Team
All Rights Reserved

---

### Post by steveo314 on 2015-06-26
I haven't used Grace yet and I'm just running through things but can you designate what handles the files in Grace? You mentioned that you use xmgrace on your Mac and I have seen other places that discuss Grace, a 'qtgrace'. Is your Ubuntu Grace using xmgrace??

---

### Post by patrickdeanmullen on 2015-06-26
Steve, 

-qtgrace is an effort to have Grace work natively on Windows and Mac OS X --  I do not use it. 

-xmgrace and grace are one in the same.  Software name: grace.  Run from Command Line: xmgrace
 
My Ubuntu Grace is downloaded from the Ubuntu Software Center and runs natively.  I hope this answers your question.

---

### Post by steveo314 on 2015-06-26
> **patrickdeanmullen said:**
> Steve, 

-qtgrace is an effort to have Grace work natively on Windows and Mac OS X --  I do not use it. 

-xmgrace and grace are one in the same.  Software name: grace.  Run from Command Line: xmgrace
 
My Ubuntu Grace is downloaded from the Ubuntu Software Center and runs natively.  I hope this answers your question.

What happens when you open one of your ubuntu created .agr 's on your Mac???

---

### Post by patrickdeanmullen on 2015-06-26
No issues whatsoever :D

If we can get it the other way around then I would be a happy man!

---

