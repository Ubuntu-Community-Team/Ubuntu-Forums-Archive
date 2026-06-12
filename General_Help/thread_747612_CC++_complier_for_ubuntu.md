---
title: "C/C++ complier for ubuntu"
date: 2008-04-06
forum: General Help
---

### Post by Brii on 2008-04-06
Where can i find one or how do i get it out of systemic and install it

---

### Post by scragar on 2008-04-06
```
sudo apt-get install build-essential
```
or, if you just want the c compiler:```
sudo apt-get install gcc
```

---

### Post by Brii on 2008-04-06
> **scragar said:**
> ```
sudo apt-get install build-essential
```
or, if you just want the c compiler:```
sudo apt-get install gcc
```

i put in the first one and now how do i get it to compile

---

### Post by pseudo-random on 2008-04-06
```
gcc sourcefile.c -o program
```
This assumes you have a program?
Google hello.cpp if you don't.

---

### Post by Brii on 2008-04-06
> **pseudo-random said:**
> ```
gcc sourcefile.c -o program
```
This assumes you have a program?
Google hello.cpp if you don't.

i put that in and it says 

brii@brii-desktop:~$ gcc sourcefile.c -o program
gcc: sourcefile.c: No such file or directory
gcc: no input files

---

### Post by scragar on 2008-04-06
replace sourcefile.c in the line with the name of the file your compiling.

---

