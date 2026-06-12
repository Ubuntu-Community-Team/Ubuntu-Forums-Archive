---
title: "libbsd library functions"
date: 2015-04-14
forum: General Help
---

### Post by e98552ba on 2015-04-14
I am currently working my way through Zed Shaw's [Learn C The Hard Way]("http://c.learncodethehardway.org/book/") and I am currently on Lesson 35.  This lesson requires the libbsd functions of 'heapsort' and 'mergesort' and I've installed the necessary libraries.  When I run my makefile to compile the lesson code, I receive an error message that tells me there is an undefined reference to the heapsort and mergesort functions.  Terminal output is below:
```
./build/liblcthw.a(darray_algos.o): In function `DArray_heapsort':
~/ex35/src/lcthw/darray_algos.c:12: undefined reference to `heapsort'
./build/liblcthw.a(darray_algos.o): In function `DArray_mergesort':
~/ex35/src/lcthw/darray_algos.c:17: undefined reference to `mergesort'
```

I'm running Lubuntu 14.04 LTS on a 64-bit Lenovo T520.

I've attached my ex35 files if they will be of assistance.  'make clean' will clean, 'make' will compile all the files, and 'make test' will run the test file.
[ATTACH]261300[/ATTACH]

---

### Post by steeldriver on 2015-04-14
Hello and welcome to the forums

The issue is almost certainly the order in which you are specifying the libraries on the link line. For example, your Makefile has

```

LDLIBS=-ldl -lbsd $(OPTLIBS)

```
and then
```

tests: LDLIBS += -lm -L./build -llcthw

```

which will result in

```

LDLIBS=-ldl -lbsd $(OPTLIBS) -lm -L./build -llcthw

```

which puts your liblcthw after the libbsd that it depends on - subordinate libraries should normally come after the objects that depend on them.

---

