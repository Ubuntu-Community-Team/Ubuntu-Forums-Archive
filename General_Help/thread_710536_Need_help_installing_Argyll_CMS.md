---
title: "Need help installing Argyll CMS"
date: 2008-02-28
forum: General Help
---

### Post by pixelnate on 2008-02-28
I am trying to install Argyll CMS on Gutsy 64-bit. I am getting errors that I cannot find out on the how to solve. Can anybody give me some pointers on getting this thing installed? This is install log:

```

Simple batch file to invoke Jam in all the subdirectories
------------
numlib
----------
...found 139 target(s)...

------------
tiff
----------
...found 239 target(s)...

------------
libusb
----------
...found 135 target(s)...

------------
libusbw
----------
...found 7 target(s)...

------------
plot
----------
...found 113 target(s)...

------------
icc
----------
...found 117 target(s)...

------------
cgats
----------
...found 106 target(s)...

------------
rspl
----------
...found 180 target(s)...

------------
gamut
----------
...found 139 target(s)...

------------
xicc
----------
...found 248 target(s)...

------------
spectro
----------
...found 288 target(s)...
...updating 8 target(s)...
Cc dispwin.o 
dispwin.c:1786: error: expected identifier or ‘(’ before ‘if’
dispwin.c:1799: error: expected identifier or ‘(’ before ‘return’
dispwin.c:1800: error: expected identifier or ‘(’ before ‘}’ token

                cc -c -DUNIX -D_THREAD_SAFE -O2  -I. -I../h -I../cgats -I../icc -I../numlib -I../xicc -I../libusb -o dispwin.o dispwin.c

...failed Cc dispwin.o ...
...skipped printread for lack of dispwin.o...
...skipped spotread for lack of dispwin.o...
...skipped filmread for lack of dispwin.o...
...skipped dispcal for lack of dispwin.o...
...skipped dispread for lack of dispwin.o...
Cc sa_dispwin.o 
dispwin.c:1786: error: expected identifier or ‘(’ before ‘if’
dispwin.c:1799: error: expected identifier or ‘(’ before ‘return’
dispwin.c:1800: error: expected identifier or ‘(’ before ‘}’ token

                cc -c -DUNIX -D_THREAD_SAFE -O2 -DSTANDALONE_TEST  -I. -I../h -I../numlib -I../cgats -I../icc -o sa_dispwin.o dispwin.c

...failed Cc sa_dispwin.o ...
...skipped dispwin for lack of sa_dispwin.o...
...failed updating 2 target(s)...
...skipped 6 target(s)...

------------
xicc
----------
...found 248 target(s)...

------------
imdi
----------
...found 151 target(s)...

------------
target
----------
...found 157 target(s)...

------------
scanin
----------
...found 113 target(s)...

------------
profile
----------
...found 171 target(s)...

------------
link
----------
...found 115 target(s)...

------------
tweak
----------
...found 104 target(s)...

------------
render
----------
...found 101 target(s)...

------------
spectro
----------
...found 288 target(s)...
...updating 8 target(s)...
Cc dispwin.o 
dispwin.c:1786: error: expected identifier or ‘(’ before ‘if’
dispwin.c:1799: error: expected identifier or ‘(’ before ‘return’
dispwin.c:1800: error: expected identifier or ‘(’ before ‘}’ token

                cc -c -DUNIX -D_THREAD_SAFE -O2  -I. -I../h -I../cgats -I../icc -I../numlib -I../xicc -I../libusb -o dispwin.o dispwin.c

...failed Cc dispwin.o ...
...skipped printread for lack of dispwin.o...
...skipped spotread for lack of dispwin.o...
...skipped filmread for lack of dispwin.o...
...skipped dispcal for lack of dispwin.o...
...skipped dispread for lack of dispwin.o...
Cc sa_dispwin.o 
dispwin.c:1786: error: expected identifier or ‘(’ before ‘if’
dispwin.c:1799: error: expected identifier or ‘(’ before ‘return’
dispwin.c:1800: error: expected identifier or ‘(’ before ‘}’ token

                cc -c -DUNIX -D_THREAD_SAFE -O2 -DSTANDALONE_TEST  -I. -I../h -I../numlib -I../cgats -I../icc -o sa_dispwin.o dispwin.c

...failed Cc sa_dispwin.o ...
...skipped dispwin for lack of sa_dispwin.o...
...failed updating 2 target(s)...
...skipped 6 target(s)...

```

---

