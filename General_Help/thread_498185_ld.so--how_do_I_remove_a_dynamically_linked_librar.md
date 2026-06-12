---
title: "ld.so--how do I remove a dynamically linked library"
date: 2007-07-11
forum: General Help
---

### Post by RyTallica898 on 2007-07-11
I sucessfully removed fglrx to revert back to the open source driver. now I get these lovely jewels every time I turn to wipe my *** in the console:

ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.

These errors rear after most commands I do.  I'm new to linux so I have no idea about environmental variables and from what I understand I need to find a way to remove this refrence to this library from ld.so. Please help me :( Im sad.

---

### Post by jordanmthomas on 2007-07-11
Try this:
```
sudo ldconfig
```
to see if it will clean itself up for you.

EDIT:  if it doesn't you might have to ask a pro about how to what to set LD_PRELOAD as.  Also, I'm glad jespdj had the same idea...makes me feel right.  :)

---

### Post by jespdj on 2007-07-11
I am not entirely sure, but I think it works like this: Dynamically linked libraries are cached somewhere by the system. If you remove the library file, it will still be somewhere in the cache. So you have to refresh the cache after deleting the library file. Try this in a terminal window:
```
sudo ldconfig -v
```
See [man page for ldconfig](http://linux.die.net/man/8/ldconfig) for more info.

Disclaimer: I'm not an expert at this.

---

