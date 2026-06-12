---
title: "C compiler"
date: 2007-01-20
forum: General Help
---

### Post by Doug11 on 2007-01-20
How can I tell if I have C compiler installed on my machine?

---

### Post by tr333 on 2007-01-20
inside a terminal type:
```
which gcc
```
this will print out the full path of the gcc compiler.
alternatively, you could just type 'gcc' and see if its found.

to find the version of the C compiler, type:
```
gcc --version
```

---

### Post by pstewart on 2007-01-20
You will need "build-essential" installed too.

```
sudo apt-get install gcc build-essential
```

---

### Post by Doug11 on 2007-01-20
this is the output i got

doug@home:~$ gcc
gcc: no input files

So this means i do not have it installed?
Now, when I run this

doug@home:~$ gcc
gcc: no input files
doug@home:~$ gcc --version
gcc (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


It seems that there is something there.

---

### Post by Jasper84 on 2007-01-20
If i need anything i just try sudo aptitude search `part name`, In the list that follows it has i's before things that are installed. (if no list follows nothing was found) Usually i can make out which are relevant. Its often better to search the web what part name should be. (because many good aps dont have obvious names. You can also use sudo aptitude show `full name` which gives more info, including description.

---

### Post by mcglnx on 2007-01-20
> **Doug11 said:**
> this is the output i got

doug@home:~$ gcc
gcc: no input files
.

gcc is a compiler. You need to pass him some c files. like hello.c 
May be you are searching for an Editor as well. Try Emacs, Eclipse or KDevelop!

HTH,
M

---

