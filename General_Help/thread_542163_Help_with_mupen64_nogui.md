---
title: "Help with mupen64_nogui"
date: 2007-09-03
forum: General Help
---

### Post by Tech_Spanky on 2007-09-03
Hello I have been trying for a week to get mupen64 compiled for nogui to use with MythGame but I just am not having any luck. The notes say I need LibSDL-devel so I went to lissdl.org and download the source. Then the usual sh autogen.sh, ./configure/ make, make install. At the end of that i get 

Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/usr/bin/install -c -m 644 build/libSDLmain.a /usr/local/lib/libSDLmain.a
ranlib /usr/local/lib/libSDLmain.a
/bin/bash ./build-scripts/mkinstalldirs /usr/local/share/aclocal
/usr/bin/install -c -m 644 ./sdl.m4 /usr/local/share/aclocal/sdl.m4
/bin/bash ./build-scripts/mkinstalldirs /usr/local/lib/pkgconfig
/usr/bin/install -c -m 644 sdl.pc /usr/local/lib/pkgconfig
/bin/bash ./build-scripts/mkinstalldirs /usr/local/share/man/man3
for src in ./docs/man3/*.3; do \
            file=`echo $src | sed -e 's|^.*/||'`; \
            /usr/bin/install -c -m 644 $src /usr/local/share/man/man3/$file; \
        done
which I am not too sure what it means. but when I switch to the mupen64_src-0.5 directory and run ./configure I get 
Found a working C compiler (gcc).
Checking SDL...
./config.temp: 3: Syntax error: "(" unexpected
*** Couldn't find a working SDL library!
dave@MythTv:~/mupen64_src-0.5$ 
It seems like the configure script does not know where my SDL library is?
I am getting really frustrated with this one. I am fairly new to linux but have been learning quickly and have accomplished a lot so far with the use of this great forum, but alsa it is my time to ask a question as I can not find the answer any where.

Thanks a lot for any help 
Dave

---

### Post by geraldm on 2007-09-03
After installing shared libraries they still are not useable because Linux works out of the
cache, and it is still using the obsolete cache.  To use the libraries, you must EITHER 
as root user enter the command "ldconfig" 
OR reboot.

On configure..
use ./configure --help
you can enter the location of packages with the parameters

./configure --with-libSDL=/usr/local
Some packages are picky, and may need "/usr/local/lib" ; experiment a bit.

Gerald

---

### Post by Tech_Spanky on 2007-09-04
Thanks for the reply. I did what you said and ran lpconfig as root and then many varients of ./configure --with-libSDL=/usr/local/lib and many others.  All return the same:

./config.temp: 3: Syntax error: "(" unexpected
*** Couldn't find a working SDL library!

Now the wierd part is that even ./configure --help returns that error.  What is with that?

And I continue.  I will get this ( with everyones help of course :) )

---

### Post by Compyx on 2007-09-04
Why not just run:
```

sudo apt-get install libsdl1.2-dev

```

Is there any reason you need to compile libsdl from source?

---

### Post by Tech_Spanky on 2007-09-04
I think I did that after I installed from source. I just followed instructions I had for mupen64. I will try that agin when I get home ( at work now).  Maybe I took the hard road :(

---

### Post by Compyx on 2007-09-04
Hmm, just tried to compile mupen64 myself and got the same error message, it'll go away if you remove the '\\n' part in line 148:
```

echo "int main(void) { if (SDL_Init( 0 ) < 0) { printf( \"SDL_Init(): %s\\n\", SDL_GetError() ); return 1; } return 0; }" >> "$FILE"

```

So it says:
```

echo "int main(void) { if (SDL_Init( 0 ) < 0) { printf( \"SDL_Init(): %s\", SDL_GetError() ); return 1; } return 0; }" >> "$FILE"

```

Apparently they screwed up with the escape-sequences and I'm too lazy to figure out how to do it correctly.
With the line altered, mupen64 builds fine on my system.

Hope this helps..

---

### Post by Tech_Spanky on 2007-09-04
Cool that worked and got me past the ./configure stage now I rum make mupen64_nogui and it says it is ready then make and this is what I get:

gcc -DX86 -O3 -fexpensive-optimizations -fomit-frame-pointer -funroll-loops -ffast-math -fno-strict-aliasing -mcpu=athlon -Wall -pipe `freetype-config --cflags` `sdl-config --cflags` -c -o blight_input/SDL_ttf.o blight_input/SDL_ttf.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
blight_input/SDL_ttf.c:52:38: error: freetype/internal/ftobjs.h: No such file or directory
blight_input/SDL_ttf.c: In function ‘TTF_OpenFontIndexRW’:
blight_input/SDL_ttf.c:279: error: dereferencing pointer to incomplete type
make: *** [blight_input/SDL_ttf.o] Error 1
root@MythTv:/home/dave/mupen64_src-0.5# 

I have installed freetype but seems the file ftobjs.h is missing. I have seach my entire system for it and can not find it.  I read on google there could be a bug with ubuntu and freetype where /freetype/internal/ftobjs.h is missing? I don't even have that directory (/internal).

Dave

---

### Post by geraldm on 2007-09-04
That program was built with freetype2 package, not the freetype package.
freetype/internal/ftobjs.h was in freetype2 which I downloaded in Dec 12, 2004
That MAY be incompatible with freetype.
You might try to find an equivalent, or updated version.

Gerald

---

### Post by jack1323 on 2007-09-09
Dave, I stumbled across the exact same problem.  After some tedious googling, I found this:

[http://bugs.sourcemage.org/show_bug.cgi?id=13630](http://bugs.sourcemage.org/show_bug.cgi?id=13630)

which led me too the patch:
[http://freetype.fis.uniroma2.it/freetype2/patches/SDL_ttf-2.0.7-noftinternals.patch](http://freetype.fis.uniroma2.it/freetype2/patches/SDL_ttf-2.0.7-noftinternals.patch)

I manually installed the patch.  That is,  I opened up SDL_ttf.c and deleted these lines starting at line 46:
< /*
< #include <freetype/freetype.h>
< #include <freetype/ftoutln.h>
< #include <freetype/ttnameid.h>
< */
< #include <freetype/internal/ftobjs.h>
< 
< #ifndef FT_OPEN_STREAM
< #define FT_OPEN_STREAM ft_open_stream
< #endif

and changed this line ( 248 ) from:
< 	stream->memory = library->memory;
to:
< 	stream->memory = NULL;

(I have no idea if the above patch will break anything, but it does get it to compile)

Everything compiled and is now working from the command line.  Now I just need to set it up with mythgame.

---

### Post by frenchn00b on 2008-02-15
Did you get more change with mupen64 no gui ?

hard to compile, developments should help a bit ... :(

---

