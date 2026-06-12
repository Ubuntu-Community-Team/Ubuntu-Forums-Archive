---
title: "$PATH quesion"
date: 2006-07-11
forum: General Help
---

### Post by lex1 on 2006-07-11
I have install some programs from source in dapper some of these source are deps for other source pacakes.

after installing each source package how do I set the $PATH
so they run from  the command line .

lex1

---

### Post by ciscosurfer on 2006-07-11
Try [this post]("http://www.ubuntuforums.org/showthread.php?t=182167&highlight=%24PATH") :D

---

### Post by lex1 on 2006-07-12
thanks for help but did not understand what they were trying to to.
still about as near to understanding as i was when i made this post.

lex1-confused :confused:

---

### Post by Titus A Duxass on 2006-07-12
Try something along the lines of:

export PATH=$PATH:/home/???

---

### Post by ayoli on 2006-07-12
another way to add a path to $PATH permanently is to edit /etc/environement file:
```
gksudo gedit /etc/environment
```
regards.

---

