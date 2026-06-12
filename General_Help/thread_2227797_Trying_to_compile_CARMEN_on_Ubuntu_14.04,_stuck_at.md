---
title: "Trying to compile CARMEN on Ubuntu 14.04, stuck at compilation error"
date: 2014-06-04
forum: General Help
---

### Post by Ken-san on 2014-06-04
Hello all, as part of my thesis I'm trying to get CARMEN (Carnegie Mellon Robot Navigation Toolkit), version 0.7.4 (last one, it seems, as it hasn't been updated since 2008) to compile and install un Ubuntu 14.04 x86. I know there are some issues with the compilation steps and I had to jump through all sorts of hoops to get to this stage, but it seems I'm stuck.

I've followed [this]("https://wiki.ubuntu.com/carmen#1004lts") (note that it's for Ubuntu 10.04) and make seemed to be working, up until compiling the Global module. Here's the trace:

```
****************************************************************
* Module  : GLOBAL
* Comment : CARMEN global functions
****************************************************************

  --> Starting make
    ---- Assigning dependencies in GLOBAL
    ---- Compiling global.c to global.o (cc)
global.c: In function ‘carmen_get_host’:
global.c:411:13: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result [-Wunused-result]
       fscanf(bin_host, "%s", hostname);
             ^
    ---- Compiling ipc_wrapper.c to ipc_wrapper.o (cc)
    ---- Compiling carmen_stdio.c to carmen_stdio.o (cc)
carmen_stdio.c: In function ‘carmen_fopen’:
carmen_stdio.c:67:17: warning: assignment from incompatible pointer type [enabled by default]
     fp->comp_fp = gzdopen(fileno(fp->fp), mode);
                 ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
carmen_stdio.c: In function ‘carmen_fgetc’:
carmen_stdio.c:84:12: error: request for member ‘have’ in something not a structure or union
     return gzgetc(fp->comp_fp);
            ^
carmen_stdio.c:84:12: error: request for member ‘have’ in something not a structure or union
     return gzgetc(fp->comp_fp);
            ^
carmen_stdio.c:84:12: error: request for member ‘pos’ in something not a structure or union
     return gzgetc(fp->comp_fp);
            ^
carmen_stdio.c:84:12: error: request for member ‘next’ in something not a structure or union
     return gzgetc(fp->comp_fp);
            ^
carmen_stdio.c:84:5: warning: passing argument 1 of ‘gzgetc’ from incompatible pointer type [enabled by default]
     return gzgetc(fp->comp_fp);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1391:21: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
 ZEXTERN int ZEXPORT gzgetc OF((gzFile file));
                     ^
carmen_stdio.c: In function ‘carmen_feof’:
carmen_stdio.c:96:5: warning: passing argument 1 of ‘gzeof’ from incompatible pointer type [enabled by default]
     return gzeof(fp->comp_fp);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1475:21: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
 ZEXTERN int ZEXPORT gzeof OF((gzFile file));
                     ^
carmen_stdio.c: In function ‘carmen_fseek’:
carmen_stdio.c:108:5: warning: passing argument 1 of ‘gzseek64’ from incompatible pointer type [enabled by default]
     return gzseek(fp->comp_fp, offset, whence);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1693:30: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
    ZEXTERN z_off64_t ZEXPORT gzseek64 OF((gzFile, z_off64_t, int));
                              ^
carmen_stdio.c: In function ‘carmen_ftell’:
carmen_stdio.c:120:5: warning: passing argument 1 of ‘gztell64’ from incompatible pointer type [enabled by default]
     return gztell(fp->comp_fp);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1694:30: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
    ZEXTERN z_off64_t ZEXPORT gztell64 OF((gzFile));
                              ^
carmen_stdio.c: In function ‘carmen_fclose’:
carmen_stdio.c:132:5: warning: passing argument 1 of ‘gzclose’ from incompatible pointer type [enabled by default]
     return gzclose(fp->comp_fp);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1511:24: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
 ZEXTERN int ZEXPORT    gzclose OF((gzFile file));
                        ^
carmen_stdio.c: In function ‘carmen_fread’:
carmen_stdio.c:144:5: warning: passing argument 1 of ‘gzread’ from incompatible pointer type [enabled by default]
     return gzread(fp->comp_fp, ptr, size * nmemb) / size;
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1313:21: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
 ZEXTERN int ZEXPORT gzread OF((gzFile file, voidp buf, unsigned len));
                     ^
carmen_stdio.c: In function ‘carmen_fwrite’:
carmen_stdio.c:157:5: warning: passing argument 1 of ‘gzwrite’ from incompatible pointer type [enabled by default]
     return gzwrite(fp->comp_fp, (void *)ptr, size * nmemb) / size;
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1341:21: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
 ZEXTERN int ZEXPORT gzwrite OF((gzFile file,
                     ^
carmen_stdio.c: In function ‘carmen_fgets’:
carmen_stdio.c:169:5: warning: passing argument 1 of ‘gzgets’ from incompatible pointer type [enabled by default]
     return gzgets(fp->comp_fp, s, size);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1372:24: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
 ZEXTERN char * ZEXPORT gzgets OF((gzFile file, char *buf, int len));
                        ^
carmen_stdio.c: In function ‘carmen_fflush’:
carmen_stdio.c:181:5: warning: passing argument 1 of ‘gzflush’ from incompatible pointer type [enabled by default]
     return gzflush(fp->fp, Z_FINISH);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1412:21: note: expected ‘gzFile’ but argument is of type ‘struct FILE *’
 ZEXTERN int ZEXPORT gzflush OF((gzFile file, int flush));
                     ^
carmen_stdio.c: In function ‘carmen_fputc’:
carmen_stdio.c:193:5: warning: passing argument 1 of ‘gzputc’ from incompatible pointer type [enabled by default]
     return gzputc(fp->comp_fp, c);
     ^
In file included from carmen_stdio.h:47:0,
                 from carmen_stdio.c:30:
/usr/include/zlib.h:1385:21: note: expected ‘gzFile’ but argument is of type ‘struct gzFile_s **’
 ZEXTERN int ZEXPORT gzputc OF((gzFile file, int c));
                     ^
carmen_stdio.c: In function ‘carmen_fgetc’:
carmen_stdio.c:88:1: warning: control reaches end of non-void function [-Wreturn-type]
 }
 ^
make[3]: *** [carmen_stdio.o] Error 1
/bin/sh: 4: exit: Illegal number: -1
make[2]: *** [libraries] Error 2
make[1]: *** [phase1] Error 2
/bin/sh: 1: exit: Illegal number: -1
make: *** [phase1] Error 2

```

As you can probably see, the errors are of the "error: request for member XXXXX in something not a structure or union" kind. I'm using gcc and g++ version 4.8.2. Latest kernel to date. Is this fixable or will I be forced to install an older version of Ubuntu to get this to work?

Thanks in advance for any help.

---

### Post by steeldriver on 2014-06-04
I've seen something like this before (with different software of similar vintage, on Ubuntu 13.10) and as far as I could tell it is a compatibility issue with the newer version(s) of zlib

I ended up installing an older version of zlib (1.2.3.5 I think - although I was not able to determine from changelogs exactly when the struct definitions changed) from the git repo into /usr/local, and configuring the build to find that ahead of the system zlib

---

### Post by tgalati4 on 2014-06-04
Creating a working build environment is the most important aspect of compiling software.  Since CARMEN was last developed in 2008, it relied on the frameworks that were available in 2008.  Trying to compile it with 2014 frameworks will be problematic.  I would set up a 10.04 environment (on a dedicated machine or a virtual machine) and try building it there.  If you are successful, then you can try porting the binary to 12.04 and see if it works.  If that works, then you try the binary on 14.04.  Understand that you may need to bring along some libraries (duplicate but older versions) on 12.04 and 14.04.

Otherwise, you need to dig into the frameworks that are causing the problem and rewrite the code to use the newer frameworks.  Then YOU become the maintainer of the code.

All of this is a lot of work measured in Agony Units.  Only you can determine if AU are worth it.

---

### Post by Robo-cop_hadu-ken on 2014-06-10
Yes I have done this on ubuntu 14.04 without zlib.h changement.
I am student of BS Software Engineering in Pakistan. contact me on this number [COLOR=#000080]_**+9203136718528**_[/COLOR]. or contact on skype_id: [COLOR=#0000cd]**ali.gush**[/COLOR]. or my site [http://www.itbuilderz.com]("http://itbuilderz.com").

---

### Post by Robo-cop_hadu-ken on 2014-06-10
I shall give you those files which I have modified on some places. carmen_stdio.c & carmen_stdio.h files. you have to replace these files with your files so you error will be eradicated. you can download these files from my website [http://itbuilderz.com/carmen/global/]("http://itbuilderz.com/carmen/global/carmen_stdio.h")
[http://itbuilderz.com/carmen/global/carmen_stdio.c](http://itbuilderz.com/carmen/global/carmen_stdio.c)

---

