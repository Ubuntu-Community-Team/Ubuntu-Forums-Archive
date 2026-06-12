---
title: "ATi RADEON Linux Driver Install Problem"
date: 2004-11-04
forum: General Help
---

### Post by amr on 2004-11-04
Hihi, Just installed Ubuntu a couple a days ago, by far the best distro I've used.

I went to the ATi website, grabbed the RADEON drivers for Linux (XFree86 4.3.0)
The check.sh file they supply on the site tells me I have 4.3.0.1

I go ahead with alien to install, and get this error.

amr@rebirth:~ $ sudo alien -i fglrx-4.3.0-3.14.1.i386.rpm
Password:
dpkg: error processing fglrx_4.3.0-4.14_i386.deb (--install):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package xlibmesa-gl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 fglrx_4.3.0-4.14_i386.deb
amr@rebirth:~ $

If you need the verbose output let me know

---

### Post by keffo on 2004-11-04
Hey

I asked about this just a few days ago, and Ulrich sent me this
turtley rocking howto

[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)


It will work.

---

### Post by amr on 2004-11-04
Thanks very much :-) it worked xD


\\:D/

---

