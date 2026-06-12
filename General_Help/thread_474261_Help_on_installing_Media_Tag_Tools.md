---
title: "Help on installing Media Tag Tools"
date: 2007-06-14
forum: General Help
---

### Post by henriquemaia on 2007-06-14
I was trying to install this app:

[http://www.kde-apps.org/content/show.php?content=35855](http://www.kde-apps.org/content/show.php?content=35855) (Media Tag Tools)

but I always get an error on make. 

On running configure, I get:

```
Verifying Qt 3.x Multithreaded (MT) build environment ... ok
Checking for taglib v1.4 or higher...scripts/config.sh: 9: cannot open 1.4: No such file
scripts/config.sh: 9: [[: not found
ok
[: 34: ==: unexpected operator
-e 
Config options
-e --------------
-e Taglib version       = 1.4
-e Prefix               = /usr/local

-e MTT version  = 0.3.2

Good, your configure finished.  Now run 'make'.
```

Upon make:

```
cd src && qmake src.pro -o Makefile
cd src && make -f Makefile
make[1]: Entering directory `/home/henriquemaia/Desktop/mediatagtools-0.3.2/src'
/usr/share/qt3/bin/uic form1.ui -o form1.h
/usr/share/qt3/bin/uic form2.ui -o form2.h
/usr/share/qt3/bin/uic about.ui -o about.h
g++ -c -pipe -Wall -W -g `taglib-config --cflags` -static -ansi -pedantic -Wno-long-long -pg -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o alistviewitem.o alistviewitem.cpp
/usr/local/include/taglib/id3v1tag.h:56: warning: ‘class TagLib::ID3v1::StringHandler’ has virtual functions but non-virtual destructor
/usr/local/include/taglib/fileref.h:89: warning: ‘class TagLib::FileRef::FileTypeResolver’ has virtual functions but non-virtual destructor
g++ -c -pipe -Wall -W -g `taglib-config --cflags` -static -ansi -pedantic -Wno-long-long -pg -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o mediatagtools.o mediatagtools.cpp
In file included from mediatagtools.cpp:1:
./config.h:1: error: stray ‘#’ in program
./config.h:1: error: expected unqualified-id before ‘-’ token
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/x86_64-linux-gnu/bits/c++config.h:47: error: ‘__gnu_debug_def’ is not a namespace-name
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../include/c++/4.1.2/x86_64-linux-gnu/bits/c++config.h:47: error: expected namespace-name before ‘;’ token
make[1]: *** [mediatagtools.o] Error 1
make[1]: Leaving directory `/home/henriquemaia/Desktop/mediatagtools-0.3.2/src'
make: *** [sub-src] Error 2

```

Any ideas on how to solve this?

---

### Post by henriquemaia on 2007-06-15
bump

---

### Post by goodtimetribe on 2007-11-04
bump from me too! This began happening after the upgrade to Gutsy.

---

### Post by minus198 on 2007-11-04
Checking for taglib v1.4 or higher...scripts/config.sh: 9: cannot open 1.4: No such file

It sounds like taglib isn't installed...

Don't know if it helps.. But the apt contains:

```
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtag1-doc - TagLib Audio Meta-Data Library [documentation]
libtag1c2a - TagLib Audio Meta-Data Library
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
libtagc0-ruby - TagLib Audio Meta-Data Library for Ruby
libtagc0-ruby1.8 - TagLib Audio Meta-Data Library for Ruby 1.8
libtaglib2.0-cil - CLI library for accessing audio and video files metadata

```

Maybe this will sort the problem: 

sudo apt-get install libtag1c2a libtag1-dev

or:

sudo apt-get install libtagc0 libtagc0-dev

---

### Post by henriquemaia on 2007-11-04
I still get the same error, albeit I have installed those packages. Thanks anyway.

---

### Post by henriquemaia on 2007-11-04
CAn someone (more knowledgeable) make a deb out of this program? I really wanted to install it. Thanks.

---

### Post by goodtimetribe on 2007-11-05
> **henriquemaia said:**
> CAn someone (more knowledgeable) make a deb out of this program? I really wanted to install it. Thanks.

I had the above packages installed as well, and still can't get MediaTagTools to compile. I've read that this was because of a problem with the repo version of the taglib. 

I was able to compile taglib and had no problems in Feisty, but I'm unable to compile [taglib]("http://developer.kde.org/~wheeler/taglib.html") since the crash, and hence can't install mediatagtools after the upgrade to Gutsy.

---

### Post by goodtimetribe on 2007-11-05
> **goodtimetribe said:**
> I had the above packages installed as well, and still can't get MediaTagTools to compile. I've read that this was because of a problem with the repo version of the taglib. 

I was able to compile taglib and had no problems in Feisty, but I'm unable to compile [taglib]("http://developer.kde.org/~wheeler/taglib.html") since the crash, and hence can't install mediatagtools after the upgrade to Gutsy.

Ok, looking into it further, it seems as though taglib is fine. it seems the problem we're having is with the ./configure script.

---

### Post by fperwth on 2008-03-11
Hi,
I had the same problem, but I think I solved it:

Just open scripts/config.sh (the one that ./configure seems to have a problem with) and change line 1 from
```
#!/bin/sh
```to```
#!/bin/bash
```

It worked for me.

---

### Post by henriquemaia on 2008-03-11
> **fperwth said:**
> Hi,
I had the same problem, but I think I solved it:

Just open scripts/config.sh (the one that ./configure seems to have a problem with) and change line 1 from
```
#!/bin/sh
```to```
#!/bin/bash
```It worked for me.

True. It worked. Thanks a lot. 

I was checking this thread a couple a days ago and I still wanted to find the solution to it. Your help comes really handy.

---

