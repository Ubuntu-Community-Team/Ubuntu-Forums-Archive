---
title: "C++ environment/compiler for Feisty?"
date: 2007-09-12
forum: General Help
---

### Post by Belinrahs on 2007-09-12
Hey,  I'm using Feisty on an x86 setup... on Windows I use Dev-C++ for my C++ programming work. It's great, and it includes a great C++ compiler. I was wondering if someone could recommend a C++ programming environment, like Dev-CPP, for Ubuntu that also has a compiler for Linux (and making sure those binaries will work on Ubuntu!). Any ideas?

---

### Post by Belinrahs on 2007-09-12
bump

---

### Post by jamvegan on 2007-09-12
The standard C++ compiler in Linux is gcc/g++.  I code in vim, so I don't really know about IDEs for Linux.  You might find helpful information in [this sticky thread]("http://ubuntuforums.org/showthread.php?t=6762") from the Programming Talk forum.

---

### Post by oddin85 on 2007-09-12
i use g++ for c++ compiling :-)

to install:
```
sudo apt-get install gcc
```

to compile:
```
g++ -o outputFile main.cpp
```

but i usually use a makefile, that way i can just type make and it'll compile for me:
```
CC = g++ ## Compiler
CFLAGS = -W -Wall -Werror -pedantic -ansi ## flags required by my classes
OBJECTS = object.o ## any objects that need to be compiled
LIBS = -lSDL ## any libraries you may need

all: main.cpp $(OBJECTS)
[INDENT]$(CC) $(CFLAGS) -o main main.cpp $(OBJECTS) $(LIBS) [/INDENT]

object.o: object.h object.cpp
[INDENT]$(CC) $(CFLAGS) -c object.cpp[/INDENT]

clean:
[INDENT]rm -f main *.o *~ *#[/INDENT]
``` 

:popcorn:

---

### Post by Ramaddan on 2007-09-13
Hi,

These are some options in terms of IDE.

1) I'm just in a hurry right now, so sorry for not looking into this properly, but I found this in a short search:
[http://sourceforge.net/project/showfiles.php?group_id=10639&package_id=15295]("http://sourceforge.net/project/showfiles.php?group_id=10639&package_id=15295")

It seems that you might be able to compile it for Linux as well, but I would encourage you otherwise, for many reasons, one of the main one being that it seems it was not updated since 2005..


2) Or you can use OpenlDev instead which is more recent and updated:

[http://www.openldev.org/download.php]("http://www.openldev.org/download.php")

There is a package you can download for i386 architecture, or compile it for other architectures.


3) Or just use Anjuta (which seems very good), that is present in the repositories through synaptic, and thus very easy to install.

Just open Synaptic and look up: **Anjuta**

Hope this helps.

---

### Post by Adramelech on 2007-09-13
Try Kdevelop anjuta is just out of beta and the version on repositories is an old one.

---

### Post by sq377 on 2007-09-13
Check out geany, it's really lightweight and works for many other formats than just c/c++.
[http://geany.uvena.de/](http://geany.uvena.de/)
It is also in the main repositories.

Better yet, try all of the ide's above and pick your favorite.

---

### Post by Belinrahs on 2007-09-13
Looked at all of them and Openldev looked like the best. Thanks for all your suggestions, it's appreciated. :)

---

### Post by stchman on 2007-09-13
> **Belinrahs said:**
> Hey,  I'm using Feisty on an x86 setup... on Windows I use Dev-C++ for my C++ programming work. It's great, and it includes a great C++ compiler. I was wondering if someone could recommend a C++ programming environment, like Dev-CPP, for Ubuntu that also has a compiler for Linux (and making sure those binaries will work on Ubuntu!). Any ideas?

gcc anf g++ are installed by default.  If you use gcc or g++ then you need to install build-essential.  There is an application called kdevelop that you can install.  There are many development tools for Linux.

---

