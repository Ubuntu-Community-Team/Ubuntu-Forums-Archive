---
title: "Problem: Dreambox compiling"
date: 2006-12-15
forum: General Help
---

### Post by pecorazza on 2006-12-15
Hi, all - nice to see ya people :D 


I have a big problem compiling a Dream Multimedia 7000 Image from cvs, using latest Ubuntu release (Efty Edge - 6.10). The DM7000 is an Open Source satellite receiving system and the OS (based on linux for ppc) can be compiled via cvs.:

By the way, I obviously installed all the needed software as shown here (via Synaptic):
[http://cvs.tuxbox.org/cgi-bin/viewcvs.cgi/tuxbox/cdk/doc/INSTALL.en?rev=HEAD](http://cvs.tuxbox.org/cgi-bin/viewcvs.cgi/tuxbox/cdk/doc/INSTALL.en?rev=HEAD)

```

-cvs
-autoconf >= 2.57a
-automake >= 1.7
- libtool >= 1.4.2
- gettext >= 0.12.1
- make >= 3.79
- makeinfo (texinfo)
- tar
- bunzip2 (bzip2)
- gunzip (gzip)
- patch
- infocmp (ncurses-bin / ncurses-devel)
-gcc 2.95 or >= 3.0
-g++ 2.95 or >= 3.0
-flex
-bison
- pkg-config
- wget
- libpng2 or libpng3 (DirectFB)

```

I had the same problem with the two previous Ubuntu releases (Dapper Drake and Breezy Badger), so I decided to test some other Linux distros such as Fedora, SuSe, Vidalinux and the copmiling went fine.

A few days ago I decided to install latest Ubuntu, and I had the same problem again. During "make dreamboximage_root", I obtain this error message:

```

   -DHAVE_INITFINI -o /root/dream/cdk/build/csu/version.o -MD -MP -MF /user/dream/cdk/build/csu/version.o.dt
In file included from version.c:33:
/user/dream/cdk/build/csu/version-info.h:1: error: missing terminating " character
/user/dream/cdk/build/csu/version-info.h:2: error: missing terminating " character
/user/dream/cdk/build/csu/version-info.h:3: error: missing terminating " character
/user/dream/cdk/build/csu/version-info.h:4: error: missing terminating " character
version.c:40: error: parse error before string constant
make[3]: *** [/user/dream/cdk/build/csu/version.o] Error 1
make[3]: Leaving directory `/user/dream/cdk/glibc-2.3.2/csu'
make[2]: *** [csu/subdir_lib] Error 2
make[2]: Leaving directory `/user/dream/cdk/glibc-2.3.2'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/user/dream/cdk/build'
make: *** [.glibc] Error 2

```

Made as well some google searches and I found an old post on a dreambox supporting board:
[http://www.sat-industry.net/forums/showpost.php?p=175158&postcount=206](http://www.sat-industry.net/forums/showpost.php?p=175158&postcount=206)
but seems that nobody knows how to do....

Can somebody please help me?

Thx

---

### Post by xopher on 2006-12-15
From CVS.. Is there a file named autogen.sh in the application directory? If so, run that before running ./configure or make.

And make sure you have the -dev versions of the dependencies installed. Eg. libpng3-dev

---

### Post by pecorazza on 2006-12-15
Thank you very much for the answer.
When I go home I will check for autogen.sh, because I am not sure if there is such a file on the home application directory.

By the way, no ./configure comand is nedded. The only comand ment to be run are these ones:

```

# export CVS_RSH=ssh
# chmod ugo+x prepare
# ./prepare dm7000
# make checkout
# make dreamboximage_root
# make rebuild-flash
# make flash-compress

```

Image, as you see, is finally compressed (using squashfs)
Yes, libng3-dev is installed :D

Thanks again

---

### Post by pecorazza on 2006-12-15
Well, tried hard to find a workaround but no joy. I ran autogen.sh before make, and checked once again libpng3...
Any other idea?

---

### Post by pecorazza on 2006-12-17
Solved. The problem was dash (where /bin/sh points)
Just rolled back to bash and everything went fine.

---

