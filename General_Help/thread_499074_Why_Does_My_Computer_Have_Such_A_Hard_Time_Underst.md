---
title: "Why Does My Computer Have Such A Hard Time Understanding The ./configure Command?"
date: 2007-07-12
forum: General Help
---

### Post by Mark76 on 2007-07-12
Everytime I use it I get the same cr*p

$ cd bbclone
:~/bbclone$ ./configure
bash: ./configure: No such file or directory
:~/bbclone$ ./configure bbclone
bash: ./configure: No such file or directory
:~/bbclone$ make
make: *** No targets specified and no makefile found. Stop.
-desktop:~/bbclone$ /configure
bash: /configure: No such file or directory
:~/bbclone$ ./config
bash: ./config: No such file or directory
-desktop:~/bbclone$ ./conf
bash: ./conf: is a directory
:~/bbclone$ sudo make install
make: *** No rule to make target `install'. Stop.
-desktop:~/bbclone$ bbclone ./configure
bash: bbclone: command not found

---

### Post by jarrett on 2007-07-12
ehh? bbclone? isn't that a php script to generate statistics for a php/html page?
I seriously doubt that it has any configure script at all...
try reading INSTALL or README file if there is one in the directory of bbclone

---

### Post by jarrett on 2007-07-12
manual @ bbclone.de :

[http://help.bbclone.de/index.php?n=Setup.HomePage]("http://help.bbclone.de/index.php?n=Setup.HomePage")

---

### Post by Mark76 on 2007-07-12
well, I downloaded it as a tar.gz file and ./configure is part of the routine for installing those.

---

### Post by jarrett on 2007-07-12
look, there ain't no configure file for this... it is a php script to be used on a webserver to display a webpage
read the help page I linked to in my previous reply

---

