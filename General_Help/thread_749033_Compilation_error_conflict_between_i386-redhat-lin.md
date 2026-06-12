---
title: "Compilation error: conflict between i386-redhat-linux - i486-linux-gnu"
date: 2008-04-08
forum: General Help
---

### Post by avners on 2008-04-08
Hi,
I am porting my stuff from an older distribution (Fedora- version 7(?)).
I can compile my sources with gcc:
gcc -c $gen/common.c++ -o $gen/common.o
compiles without problems.

But when I try this with "make" I get:
make $gen/common.o
make: *** No rule to make target `/usr/lib/gcc/i386-redhat-linux/3.4.2/include/stddef.h', needed by `/home/avner/source/lib/general/common.o'.  Stop.

And that makes sense, since under /usr/lib/gcc I have only this:
la /usr/lib/gcc/
total 4
drwxr-xr-x 4 root root 4096 2008-04-04 17:43 i486-linux-gnu

Can you help me detect the problem? Should I re-configure "make" ?
How can I do that? Why is it looking for /usr/lib/gcc/i386-redhat-linux
in the first place?

Thanks, Avner.

---

### Post by dcstar on 2008-04-08
> **avners said:**
> Hi,
I am porting my stuff from an older distribution (Fedora- version 7(?)).
I can compile my sources with gcc:
........
Can you help me detect the problem? Should I re-configure "make" ?
How can I do that?** Why is it looking for[B] /usr/lib/gcc/i386-redhat-linux**[/B]
in the first place?


Because the software is configured that way - it has components set for that distro, not this one.

---

### Post by avners on 2008-04-09
Thanks for your reply.

But this is the "make" program from my newly installed distribution!
Are you saying the distribution I have isn't consistent?
How can I configure "make" to function correctly (according to my
current directory tree) ?

---

