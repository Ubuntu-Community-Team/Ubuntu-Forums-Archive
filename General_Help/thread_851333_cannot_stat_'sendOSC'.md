---
title: "cannot stat 'sendOSC'"
date: 2008-07-06
forum: General Help
---

### Post by dodle on 2008-07-06
I'm getting this error while compiling LiVES from source:> /usr/bin/install: cannot stat `sendOSC': No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/applications/lives/libOSC/sendOSC'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/applications/lives/libOSC'
make: *** [install-recursive] Error 1


---

### Post by wrojr on 2009-01-21
You could try 

./configure -disable-OSC

and it compiles.

OSC is a program to control (or exchange messages, I don't
know) with the LiVES.

Bye!!!!

---

