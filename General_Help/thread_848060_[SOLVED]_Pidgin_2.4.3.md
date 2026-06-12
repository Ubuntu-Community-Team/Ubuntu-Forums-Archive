---
title: "[SOLVED] Pidgin 2.4.3"
date: 2008-07-03
forum: General Help
---

### Post by Plasma_NZ on 2008-07-03
ok, iim runing pidgin fromt he hardy repo's - but there's been updates to pdigin to fix memory leaks etc.. now i cant login to icq etc due to it stating my pidgiin is out of date...

Current version is 2.4.1 - new is 2.4.3 with the memory leak fix's - tried doin a "make" "./configure" "make install" with no success

Any idea's.?

im aware hardy doesnt put new versions of app's in the repo's, but seen as though this update fix's issues with the client.. whats the chances of this happeing..

if someone can help, cheers..

---

### Post by doorman on 2008-07-03
> **Plasma_NZ said:**
> tried doin a "make" "./configure" "make install" with no success
Maybe reverse order?
Try:
```
$ ./configure
$ make
$ sudo make install
```
This one should work. Also, if during configure you get an error, means you have to install some dependencies first ( configure usually tells what is missing )

---

### Post by Plasma_NZ on 2008-07-03
none of that worked.. tried... but found another post regarding this, which solved my issue..

[http://ubuntuforums.org/showthread.php?t=847531](http://ubuntuforums.org/showthread.php?t=847531)

---

