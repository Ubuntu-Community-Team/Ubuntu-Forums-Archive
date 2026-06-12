---
title: "Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion"
date: 2014-02-12
forum: General Help
---

### Post by pixelro on 2014-02-12
Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!

Box2D builds fine on Ubuntu 14.04 but i get this error when running ~/Box2D_v2.1.2/Box2D/Build/Testbed$ ./Testbed 

i don't even... :confused:

---

### Post by arealperson on 2014-04-21
Did you get this fixed, How did you fix it ?

Its my understanding that this is a bug in 13.10 and UP, Your out of luck. no one currently has a solution.
maybe someday in the future you'll be able to compile OpenGL on Ubuntu.

I've just installed 14.04 and have the same problem.

You might try...sudo 
$ sudo ln -s /usr/lib/nvidia-319/libGL.so /usr/lib/x86_64-linux-gnu/

But that will only work for a few people.

My advise is 'delete Ubuntu' and revert to 12.04.

If someone knows how to fix this , it would be nice if they would post the solution
or point to a URL

---

### Post by cariboo on 2014-04-21
Moved to General Help, seeing as trusty has been released.

---

