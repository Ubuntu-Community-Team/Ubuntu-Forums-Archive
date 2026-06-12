---
title: "How do I use gcc?"
date: 2005-08-08
forum: General Help
---

### Post by smnisme01 on 2005-08-08
If I write a C source file, how do I compile it?
How do I use gcc?

---

### Post by jeremytaylor on 2005-08-08
The most basic command will look something like

gcc sourcefile.c -o program-name

then you might get fancy and want to link libraries and things but i suggest looking at the man pages for that.

jeremy

---

### Post by johanvdw on 2005-08-08
If it is just a small program:
[http://galton.uchicago.edu/~gosset/Compdocs/gcc.html](http://galton.uchicago.edu/~gosset/Compdocs/gcc.html)
[http://www.google.com/search?q=gcc+tutorial](http://www.google.com/search?q=gcc+tutorial)
Once you want to compile larger applications it's best to use makefiles (kind of batchfiles used to compile programs). You can look at makefiles supplied by other programs and search for help on google, but I recommend you to learn it from a book. 

By default gcc is not installed in ubuntu. You can install it though by running:
```
sudo apt-get install build-essential
```
in a console window.

---

### Post by smnisme01 on 2005-08-08
Thanks for the info. Are there many important applications that Ubuntu does not install by default? How can I find out what they are?

---

### Post by Lord Illidan on 2005-08-08
Check on the ubuntuguide [www.ubuntuguide.org](http://www.ubuntuguide.org) 

Browsing synaptic is also useful...

---

