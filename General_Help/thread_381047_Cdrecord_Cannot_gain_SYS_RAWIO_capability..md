---
title: "Cdrecord: Cannot gain SYS_RAWIO capability."
date: 2007-03-10
forum: General Help
---

### Post by rocketman768 on 2007-03-10
Hey all. I can only burn CD-Rs at 4x speed even though my burner is a 48x burner. I believe the problem is that I "cannot gain the SYS_RAWIO capability." Some threads say to install cdrecord as suid root. I've done this, and still the same problem. I'm using kernel 2.6.18.6. Here is the output from cdrecord -scanbus:

```

Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.18.6
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.34
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'ATA     ' 'WDC WD2500KS-00M' '02.0' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *


```

---

### Post by rocketman768 on 2007-03-10
Also, I am running "sudo cdrecord".

---

### Post by rocketman768 on 2007-03-10
Please help?

---

### Post by rocketman768 on 2007-03-10
Alright, nevermind I gues...

:icon_frown: 
](*,)

---

### Post by ubeauty on 2007-04-07
Mine seems to work fine, although I note the message > Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted  - I'm using gnomebaker as a user (not root).

---

