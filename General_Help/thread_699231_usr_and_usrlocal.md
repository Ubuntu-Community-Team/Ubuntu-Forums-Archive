---
title: "/usr and /usr/local"
date: 2008-02-17
forum: General Help
---

### Post by Mr.Johnny on 2008-02-17
Hi!

Is there any problem about changing the prefix to /usr when in the makefile says /usr/local? And if I change that, is it necessary to change something else in it?

Thanks

---

### Post by drocko on 2008-02-17
There's not necessarily a problem in changing that, but each package will be different so you may have to do some research. The way to make this change is by adding it as a flag to the configure script that builds the makefile. 

Why do you want to make this change though? /usr is for things that come with the distribution and it sounds like you're compiling something from source so I don't imagine it comes with Ubuntu. Tradition says that this should go into /usr/local.

---

### Post by zvacet on 2008-02-17
```
 ./configure --prefix= /usr
```

---

### Post by Mr.Johnny on 2008-02-17
The problem I found was with dependencies, some other programs couldn't find the libs in /usr/local.

---

### Post by geraldm on 2008-02-17
After installing the libraries, you still need to provide access to those libraries.
Linux works out of a cache, and to flush the cache, you can 1) reboot, OR 2) execute "sudo ldconfig"
You may still need to be aware of the environment variables, such as "LD_LIBRARY_PATH"
and also adjust the PATH for some programs.

Gerald

---

### Post by Mr.Johnny on 2008-02-18
Hmm, I see... still learning :D 

Don't laugh, but where do I set the environment variables? :oops:

---

