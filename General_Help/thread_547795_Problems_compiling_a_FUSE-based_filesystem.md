---
title: "Problems compiling a FUSE-based filesystem"
date: 2007-09-10
forum: General Help
---

### Post by qscomputing on 2007-09-10
Hi,

(Not sure if this is the appropriate board, mods please move if not.)

I'm trying to compile a FUSE-based filesystem "SieFS", but make fails with the following error (relevant section in bold):

> <snip>
gcc  -I/usr/include -DFUSEINST="\"/usr\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22  -L/lib -o siefs  siefs.o obex.o transport.o comm.o crcmodel.o charset.o /usr/lib/libfuse.a -lpthread 
[b]/usr/lib/libfuse.a(fuse.o): In function `curr_time':
(.text+0xf56): undefined reference to `clock_gettime'
/usr/lib/libfuse.a(fuse.o): In function `curr_time':
(.text+0xf88): undefined reference to `clock_gettime'[/b]
collect2: ld returned 1 exit status
make[2]: *** [siefs] Error 1
make[2]: Leaving directory `/home/qscomputing/downloads/siefs-0.5/siefs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/qscomputing/downloads/siefs-0.5'
make: *** [all] Error 2


So which dev packages should I install to get the appropriate headers for clock_gettime - or how else should I go about fixing the problem?

Thanks very much,
  QS.

---

### Post by AndersRiggelsen on 2007-09-11
Actually I have the exact same make error. Any help would be appreciated :)
Just got a new cellphone and need to extract everything from my old one to my computer to put it back on the new one.

---

### Post by qscomputing on 2007-09-12
A bit of poking around suggests its a problem with the FUSE headers supplied by Ubuntu. I will keep trying, but it may be a case of compiling FUSE from source as well. :-(

---

### Post by qscomputing on 2007-09-18
OK, I have found a fix, detailed below. It's not the most elegant of solutions, but it works. Maybe someone who understands Makefiles a bit better than me ought to create the appropriate patch and submit it to the maintainer.

I have now successfully built and run siefs. I was able to mount my phone (C75) and browse it using command line and my favourite file manager (ROX). I didn't try to open any files or write anything to the phone. However, there is currently no reason to assume that these won't work, as I have got SieFS working with this computer and phone before using a different distro. It is a little unreliable (as in, it doesn't always read the phone first time, but generally works eventually) but that is nothing new either, and I suspect that is my hardware more than anything.

The problem is that using the function curr_time requires the program to be linked against librt. This can be acheived by adding "-lrt" to the command where gcc is run to compile siefs. As I said above, there is no doubt a correct way to do that; this isn't the most correct way, but it works for me:

Run ./configure, then open ./siefs/Makefile in your favourite editor. Edit line 82 by adding the bold text:
> CFLAGS = -I$(fuseinst)/include -DFUSEINST="\"$(fuseinst)\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 **-lrt**

There is probably a more appropriate place to add this, (a) because this will link the rt library to every executable produced, making them larger, and (b) because the Makefile is auto-generated. It seems to work for me, your mileage may vary.

HTH,
  QS.

---

### Post by zhangxxx on 2008-05-18
help...........ubuntu 8.04
I don't know how to fix it.

> make  all-recursive
make[1]: Entering directory `/home/zxzyzw/&#19979;&#36733;/siefs-0.5'
Making all in siefs
make[2]: Entering directory `/home/zxzyzw/&#19979;&#36733;/siefs-0.5/siefs'
gcc  -I/usr/include -DFUSEINST="\"/usr\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22  -L/lib -o siefs  siefs.o obex.o transport.o comm.o crcmodel.o charset.o /usr/lib/libfuse.a -lpthread 
/usr/lib/libfuse.a(fuse.o): In function `curr_time':
(.text+0x2116): undefined reference to `clock_gettime'
/usr/lib/libfuse.a(fuse.o): In function `curr_time':
(.text+0x2148): undefined reference to `clock_gettime'
/usr/lib/libfuse.a(fuse.o): In function `fuse_put_module':
(.text+0x2df5): undefined reference to `dlclose'[QUOTE]
/usr/lib/libfuse.a(fuse.o): In function `fuse_new_common':
(.text+0x3349): undefined reference to `dlopen'
/usr/lib/libfuse.a(fuse.o): In function `fuse_new_common':
(.text+0x36a1): undefined reference to `dlerror'
/usr/lib/libfuse.a(fuse.o): In function `fuse_new_common':
(.text+0x36c8): undefined reference to `dlclose'
collect2: ld &#36820;&#22238; 1
make[2]: *** [siefs] &#38169;&#35823; 1
make[2]: Leaving directory `/home/zxzyzw/&#19979;&#36733;/siefs-0.5/siefs'
make[1]: *** [all-recursive] &#38169;&#35823; 1
make[1]: Leaving directory `/home/zxzyzw/&#19979;&#36733;/siefs-0.5'
make: *** [all] &#38169;&#35823; 2[/QUOTE]

---

