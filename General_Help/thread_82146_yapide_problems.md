---
title: "yapide problems"
date: 2005-10-26
forum: General Help
---

### Post by nrayever on 2005-10-26
i was looking for a good ide program for pic16f84 simulation. googling for the web i found YaPIDE and has most of the characteristics of a winbugz similar program.

but while i try to compile it i got some errors:

```

nrayever@NFORCE:~$ cd Desktop/YaPIDE-0.1
nrayever@NFORCE:~/Desktop/YaPIDE-0.1$ ./configure
*******************************************************************************
 QTDIR is not set. This package requires a correctly set up
 qt. To get qt visit http://www.trolltech.com
*******************************************************************************
nrayever@NFORCE:~/Desktop/YaPIDE-0.1$

```

i'm using kubuntu/ubuntu amd64. according to the installation requirements, my linux box need to have QT, GCC and gpasm, programs that i installed before trying to compile. can someone help me to solve this problem?? this is the homepage for yapide:

[http://www.mtoussaint.de/yapide.html]("http://www.mtoussaint.de/yapide.html")

i really need this program, i hope someone help me!!

sincerly nrayever

---

### Post by Data_ on 2007-08-26
open a terminal an type this:
export QTDIR=/usr/share/qt3

you can now made a ./configure

---

