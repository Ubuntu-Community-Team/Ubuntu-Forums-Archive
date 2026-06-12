---
title: "Help Installing e2salvage"
date: 2008-05-12
forum: General Help
---

### Post by the ev on 2008-05-12
I can't seem to install this program.  Here's what I get when I try to run "make":

```
evan@evan-heron:~/Desktop/e2salvage-0.0.8a$ make
make  all-recursive
make[1]: Entering directory `/home/evan/Desktop/e2salvage-0.0.8a'
Making all in src
make[2]: Entering directory `/home/evan/Desktop/e2salvage-0.0.8a/src'
source='main.c' object='main.o' libtool=no \
	DEPDIR=.deps depmode=none /bin/sh ../depcomp \
	gcc -DHAVE_CONFIG_H -I. -I..     -Wall -c main.c
main.c: In function ‘main’:
main.c:45: error: storage size of ‘geob’ isn’t known
main.c:86: warning: implicit declaration of function ‘open’
main.c:99: error: ‘HDIO_GETGEO_BIG’ undeclared (first use in this function)
main.c:99: error: (Each undeclared identifier is reported only once
main.c:99: error: for each function it appears in.)
main.c:112: warning: implicit declaration of function ‘fstat64’
main.c:45: warning: unused variable ‘geob’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/evan/Desktop/e2salvage-0.0.8a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/evan/Desktop/e2salvage-0.0.8a'
make: *** [all] Error 2

```

What am I doing wrong? Any suggestions?  Thanks for the help!

---

### Post by wpagnon on 2010-10-12
Well Well,

I know it is about 2 years from the start of this post so I might not help you directly but case somebody is stuck to this problem .. I thought as I just resolved it give so information about debugging e2salvage.

first of all you do notthing wrong here are what you have to change in the code to start ddebug the part where you was at:

comment the following lines in main.c:

 
struct hd_big_geometry geob;

and

 if (ioctl(i, HDIO_GETGEO_BIG, &geob) == 0) { 
  fs_size = (unsigned long long) geob.heads 
  (unsigned long long) geob.sectors 
  (unsigned long long) geob.cylinders 
  512ull; 
 } 
 else 
then add in main.h for the _32 problem:

#include <asm/types.h>

then add in main.c, salvage_dir_inodes.c,salvage_dir_blocks.c,find_dirs.c
that complain about  linux/ext2_fs.h

add above its include:

#include <linux/fs.h>

then in dirops.c

remove (void *) for dirent += dirent->rec_len.

that should help to pass make and make install

cheers,

William

[www.freelancerobotics.com.au](www.freelancerobotics.com.au)

---

