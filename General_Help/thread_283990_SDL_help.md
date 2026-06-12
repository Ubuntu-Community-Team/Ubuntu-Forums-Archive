---
title: "SDL help"
date: 2006-10-24
forum: General Help
---

### Post by BlocknBleed on 2006-10-24
Hey, trying to install one thing leads to another andanother and another.
Problem right now is SDL_image-1.2.5
I did the ./configure 
 and then  make
I got this error
............libs/IMG_xpm.o .libs/IMG_xv.o  -Wl,--rpath -Wl,/usr/local/lib -Wl,--rpath -Wl,/usr/local/lib -lpng -ljpeg -ltiff -lz -L/usr/local/lib /usr/local/lib/libSDL.so -lpthread  -Wl,-rpath -Wl,/usr/local/lib -Wl,-soname -Wl,libSDL_image-1.2.so.0 -o .libs/libSDL_image-1.2.so.0.1.4
/usr/bin/ld: cannot find -ljpeg
collect2: ld returned 1 exit status
make: *** [libSDL_image.la] Error 1

Anyone else been through this SDL bullsh!t?

---

### Post by lloyd_b on 2006-10-25
> Hey, trying to install one thing leads to another andanother and another.
Problem right now is SDL_image-1.2.5
I did the ./configure
and then make
I got this error
............libs/IMG_xpm.o .libs/IMG_xv.o -Wl,--rpath -Wl,/usr/local/lib -Wl,--rpath -Wl,/usr/local/lib -lpng -ljpeg -ltiff -lz -L/usr/local/lib /usr/local/lib/libSDL.so -lpthread -Wl,-rpath -Wl,/usr/local/lib -Wl,-soname -Wl,libSDL_image-1.2.so.0 -o .libs/libSDL_image-1.2.so.0.1.4
/usr/bin/ld: cannot find -ljpeg
collect2: ld returned 1 exit status
make: *** [libSDL_image.la] Error 1

Anyone else been through this SDL bullsh!t?

I haven't messed ith SDL_image, but I do recognize that error message.  You need to install a package called "libjpeg" (and it's companion, "libjpeg-dev").  (The current versions are "libjpeg62" and "libjpeg62-dev"). 

There's a problem with the "configure" for that program - if it needs libjpeg, it should have detected that it was missing when you ran "./configure".  Complain to the maintainer of the program about that.

Lloyd B.

---

### Post by BlocknBleed on 2006-10-25
thanks for the help

---

