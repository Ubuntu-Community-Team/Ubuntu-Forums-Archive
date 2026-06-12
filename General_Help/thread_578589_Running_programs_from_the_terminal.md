---
title: "Running programs from the terminal"
date: 2007-10-17
forum: General Help
---

### Post by enchance on 2007-10-17
Just curious,  but how does ubuntu know which program to run? Is there like a list or a folder somewhere which it follows?

---

### Post by maybeway36 on 2007-10-17
There is a list of places in which it looks (the PATH variable) which includes /bin, /sbin/ usr/bin, /usr/local/bin, etc.

---

### Post by cmnorton on 2007-10-17
Your PATH environment variable determins this. If your current directory is not in your path, you reference the path to your program using ./your_program.

---

### Post by LanDan on 2007-10-17
you mean when you start your computer? or when you start firefox?

the programs are under /usr/bin and /usr/sbin

/usr/bin/firefox for example

---

### Post by ThrobbingBrain66 on 2007-10-17
I don't know how "correct" it is to say it this way, but almost everything executable is located in either /bin/ or /usr/bin/

You'll find mostly bash commands in /bin/ while /usr/bin/ contains mostly installed package binaries.

---

### Post by bodhi.zazen on 2007-10-17
> **enchance said:**
> Just curious,  but how does ubuntu know which program to run? Is there like a list or a folder somewhere which it follows?

See these links for an overview of the file system :

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)  

[http://freeos.com/articles/3102/](http://freeos.com/articles/3102/)

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

