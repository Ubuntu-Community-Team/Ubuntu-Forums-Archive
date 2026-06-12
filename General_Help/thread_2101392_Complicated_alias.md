---
title: "Complicated alias"
date: 2013-01-04
forum: General Help
---

### Post by dlp21 on 2013-01-04
I want to setup an alias so that I don't have to write:

```
gcc -o filename filename.c `pkg-config --cflags --libs gtk+-3.0`
```

So that I can just write:

```
gtk filename.c
```

The main problem is that filename.c has to come before the backticks, otherwise this would be simple.

---

### Post by steeldriver on 2013-01-04
I think you will probably need to define a shell function rather than an alias

```
$ function mycc { gcc -o "${1%.*}" "$1" ; }; export -f mycc
$ 
$ mycc hello.c
$ 
$ ./hello
Hello World Version 5

```

---

### Post by Impavidus on 2013-01-04
For compiling most people use a Makefile.

---

### Post by steeldriver on 2013-01-04
^^^ true dat - sometimes I don't see the wood for the trees ):P

dwhitney67 has previously posted some nice clean minimal Makefiles that would make a great starting point - e.g. this one's for C++ but you get the idea: 

[http://ubuntuforums.org/showpost.php?p=12427234&postcount=2](http://ubuntuforums.org/showpost.php?p=12427234&postcount=2)

---

### Post by dlp21 on 2013-01-04
Yep, makefile it is.

---

