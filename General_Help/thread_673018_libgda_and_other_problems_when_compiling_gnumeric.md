---
title: "libgda and other problems when compiling gnumeric"
date: 2008-01-20
forum: General Help
---

### Post by erik00270 on 2008-01-20
Dear all,

I am compiling gnumeric after I modified the gnumeric.h file to make the maximum number of rows twice as big (about 130 000) as the default. I also changed the max nro of columns twice as small (128) as the default.

When I run ../configure in src folder I get: 

        Perl Support:           yes (using perl)
        Python Support:         yes (using python)

        GDA support:            NO.  libgda problem
        GNOME-DB support:       no
        Psiconv support:        missing dependencies

I have checked that I have everything gnumeric depends on as it is said: 

[http://packages.ubuntu.com/dapper/math/gnumeric](http://packages.ubuntu.com/dapper/math/gnumeric)     (1)

and everything seemed fine except that I noticed that my ligoffice-0-4 version is 0.4.2-ubuntu1 even though the web page (1) tells that gnumeric depends on libgoffice-1-2 version >0.2.1

But how do I get that package (libgoffice-1-2) with ease? 

I have usually used the Synaptic Package Manegement program Synaptic0.60ubuntu5 for installing new packages.

My Ubuntu release is 7.10 (gutsy)
Kernel Linux 2.6.22-14-generic
GNOME 2.20.1

Suggestions?

Also if the same modification (increasing the maximum number of rows) is easier done in e.g. open office calc I can try to do that.

Thx!
Erik

---

### Post by erik00270 on 2008-01-26
This solved the problem:
[http://blog.firetree.net/2005/12/08/building-debian-packages-from-source/](http://blog.firetree.net/2005/12/08/building-debian-packages-from-source/)

---

