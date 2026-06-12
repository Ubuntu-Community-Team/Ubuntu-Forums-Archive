---
title: "vuescan core dumped on Edgy"
date: 2006-11-11
forum: General Help
---

### Post by &#40657;&#38632;BR on 2006-11-11
Hello 

I am trying to fire up vuescan, but it core dumped up on start up :confused: 

Is there anyone using vuescan on Edgy ?


The following is a strace log.


Thank you for your help :-D

---

### Post by lawrencegold on 2006-11-21
> **??BR said:**
> Hello 

I am trying to fire up vuescan, but it core dumped up on start up :confused: 

Is there anyone using vuescan on Edgy ?

Thank you for your help :-D

I haven't tried it yet with Edgy, but I've had a startup problem on Gentoo, apparently because of a double-free. I can't get your strace to download, so I don't know if this'll help, but try launching it like so:

    MALLOC_CHECK_=0 ./vuescan

I have to do this the first time I run vuescan after turning on my scanner. Subsequently, it'll work without adjusting MALLOC_CHECK_. I'm reporting this problem to the author later today.

---

### Post by lewiz on 2007-05-09
*bump*  :)

I had this same problem, dug a little deeper and found (I think) that VueScan is incompatible with glibc 2.5:

```
$ gdb ./vuescan
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you
are
welcome to change it and/or distribute copies of it under certain
conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for
details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) run
(no debugging symbols found)
[snip snip]
[Thread debugging using libthread_db enabled]
[New Thread -1219413808 (LWP 8735)]
(no debugging symbols found)
[snip snip]
Program received signal SIGSEGV, Segmentation fault.
---Type <return> to continue, or q <return> to quit---
[Switching to Thread -1219413808 (LWP 8735)]
0xb77b1e1b in free () from /lib/tls/i686/cmov/libc.so.6
(gdb) 
```

I emailed Ed Hamrick about this and he suggested that I switch to Mac OS X :P

But seriously... does anybody else have any suggestions as to how to get this going?  I'd really quite like to give VueScan a spin!

---

