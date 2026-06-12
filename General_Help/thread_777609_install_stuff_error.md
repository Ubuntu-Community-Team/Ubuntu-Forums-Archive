---
title: "install stuff error"
date: 2008-05-01
forum: General Help
---

### Post by dluu13 on 2008-05-01
I have this stuff that I want to install.

mupen64 to be exact.  I downloaded the sourcecode, and I can't ./configure it.

It doesn't work for other programs either.  I can't think of any other ones right now, but I'm getting these sorts of errors.

> *** Couldn't compile test program.
*** Couldn't find a working C compiler!

I've gone to the synaptic package manager and tried to find c compilers.  I've installed the ones I could find and it still gives me that message.  I'm trying to do this on my own computer (running ubuntu) and I get this sort of error as well.  It goes through the normal stuff, but I still have trouble finding the c compiler.

Does anybody know whether this is actually a problem with a c compiler?

---

### Post by Monicker on 2008-05-01
sudo apt-get install build-essential


That will give you everything you need to compile.  Are there any specific dependencies listed in the README or INSTALL file for the program?

---

### Post by dluu13 on 2008-05-01
Oh, okay thanks.  I'll try that

EDIT: I don't see any special requirements in the README.

Also, it can't find a working sdl library now.

---

