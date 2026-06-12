---
title: "gcc problem"
date: 2008-05-06
forum: General Help
---

### Post by htpvitas on 2008-05-06
when my using gcc to build my grogram, the problem has been occur:

htpvitas@root:~/Desktop/program/example$ ls
m.c  m.c~
htpvitas@root:~/Desktop/program/example$ gcc -o m m.c
m.c:1:18: error: stdio.h: No such file or directory
m.c: In function ‘main’:
m.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

who can tell me? thank you!

---

### Post by Damanther on 2008-05-06
You might want to post the contents of your m.c file. You might make sure you have build-essentials installed as well. You either have a syntax error or are missing the standard includes that go with gcc.

---

### Post by retrow on 2008-05-06
Considering that your program has correct syntax, you should,
```
sudo apt-get install build-essential
```That should let you compile and build successfully.

---

