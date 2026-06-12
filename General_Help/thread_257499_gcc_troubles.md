---
title: "gcc troubles"
date: 2006-09-14
forum: General Help
---

### Post by welshboy on 2006-09-14
Hi,

I'm trying to write C programs in Ubuntu, and I've installed gcc properly through Synaptic, yet I've just tried writing a simple hello world program, and I get the following error messages:

hello.c:1:18: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

I'm not sure why this is happening, I've installed all the libraries I can think of, any help would be very very much appreciated.

welshboy

---

### Post by cstudent on 2006-09-14
Try installing the build-essential package. It should give you whatever you are missing.

---

### Post by welshboy on 2006-09-14
Sir, you are a true friend!

That was just what was needed.  I'll get the hang of this at some point I'm sure.

Many thanks indeed.

welshboy

---

