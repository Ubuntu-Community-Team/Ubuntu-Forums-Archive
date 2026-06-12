---
title: "Trouble setting up Fusepython"
date: 2008-01-31
forum: General Help
---

### Post by tickingaway on 2008-01-31
I want to try Wikipediafs out, but in order to do so I need to install Fusepython.
When I run "python setup.py install"  it get's this far:

running install
running build
running build_py
creating build
creating build/lib.linux-i686-2.5
copying fuse.py -> build/lib.linux-i686-2.5
creating build/lib.linux-i686-2.5/fuseparts
copying fuseparts/__init__.py -> build/lib.linux-i686-2.5/fuseparts
copying fuseparts/subbedopts.py -> build/lib.linux-i686-2.5/fuseparts
copying fuseparts/setcompatwrap.py -> build/lib.linux-i686-2.5/fuseparts
running build_ext
building 'fuseparts._fusemodule' extension
creating build/temp.linux-i686-2.5
creating build/temp.linux-i686-2.5/fuseparts
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/fuse -I/usr/include/python2.5 -c fuseparts/_fusemodule.c -o build/temp.linux-i686-2.5/fuseparts/_fusemodule.o -D_FILE_OFFSET_BITS=64

And then it starts spitting out errors.  They all seem to be coming from /fuseparts/_fusemodule.c .  A few examples are:
fuseparts/_fusemodule.c:873: error: ‘PyObject’ has no member named ‘ob_refcnt’
fuseparts/_fusemodule.c:873: error: ‘PyObject’ has no member named ‘ob_type’
fuseparts/_fusemodule.c:960: error: invalid lvalue in increment
fuseparts/_fusemodule.c:960: warning: statement with no effect

I don't really know what the problem might be, so I don't know what other information would be relevant.  Any help would be appreciated, thank you.

---

### Post by Steveway on 2008-01-31
I think I just saw it in the repos while I was looking for another python-package.
So just open up Synaptic and search for python and scroll through that till you see it.

---

### Post by tickingaway on 2008-01-31
Thanks for the tip, but I don't see it in there.

Do you know if it was on a third-party repository?  I don't really have any of those set up at the moment.

---

### Post by tickingaway on 2008-01-31
I was able to install the bindings.  My problem involved gcc.
I resolved it by reading this post:

[http://ubuntuforums.org/showthread.php?t=17033&page=2](http://ubuntuforums.org/showthread.php?t=17033&page=2)

---

### Post by Steveway on 2008-01-31
It's in Universe. So a sudo apt-get install python-fuse should install it.
Good that you solved it yourselve, but don't forget that the package-manager is the preferred way to install anything, just for the future.

---

