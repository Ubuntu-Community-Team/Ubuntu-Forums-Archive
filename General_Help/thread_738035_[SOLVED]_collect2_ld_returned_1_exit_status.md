---
title: "[SOLVED] collect2: ld returned 1 exit status"
date: 2008-03-28
forum: General Help
---

### Post by paolo.komninidis on 2008-03-28
Hi to all, i have a problem when i try to compile my program.
Here is the output:

root@ubuntu:# make
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o main.o main.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o serpent.o serpent.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o mondo.o mondo.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o punto.o punto.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o globject.o globject.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o alimento.o alimento.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o ostacolo.o ostacolo.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o glmaterial.o glmaterial.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o auxiliar.o auxiliar.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o model.o model.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o alcool.o alcool.cc
g++ -I/usr/X11R6/include -I/tmp/usr/include -Wall      -c -o display.o display.cc
g++ -g main.o serpent.o mondo.o punto.o globject.o alimento.o ostacolo.o glmaterial.o auxiliar.o model.o alcool.o display.o -o serpent -L/usr/X11R6/lib -L/tmp/usr/lib -lGL -lGLU -lglut -lgd -lpng -lz -ljpeg -lfreetype -lm
/usr/bin/ld: cannot find -lgd
collect2: ld returned 1 exit status
make: *** [serpent] Error 1


Can anyone help me please?i have no idea what seems to be the problem. I have already tried to set LD_LIBRARY_PATH manually through .bashrc.

This is the Makefile:

CPP  = g++ -g

CC   = gcc

OBJ  = main.o serpent.o mondo.o punto.o globject.o alimento.o ostacolo.o glmaterial.o auxiliar.o model.o alcool.o display.o

LINKOBJ  = ${OBJ}

LGD  = -lgd -lpng -lz -ljpeg -lfreetype -lm

LIBS = -L/usr/X11R6/lib -L/tmp/usr/lib -lGL -lGLU -lglut $(LGD)

INCS = -I/usr/X11R6/include -I/tmp/usr/include

BIN  = serpent

CFLAGS = $(INCS) -Wall 

CXXFLAGS = $(CFLAGS) $(EXTRA) 

RM = rm -f



.PHONY: all all-before all-after clean clean-custom



all: all-before $(BIN) all-after





clean: clean-custom

	${RM} $(OBJ) $(BIN)



$(BIN): $(OBJ)

	$(CPP) $(LINKOBJ) -o $(BIN) $(LIBS)


I need your help....

---

### Post by lloyd_b on 2008-03-28
Here's the critical message:
```
/usr/bin/ld: cannot find -lgd
```

This is telling you that it's trying to link to "-lgd" (which would be a file called "libgd.so"), but it's unable to find this library.

Hmmm - "apt-file" comes up with *two* sets of packages that will install the needed file(s) - either "libgd2-noxpm" and "libgd2-noxpm-dev", or "libgd2-xpm" and "libgd2-xpm-dev".

Pick whichever set you think is correct (I have no clue) and install them, then try the compile again.

Lloyd B.

---

### Post by paolo.komninidis on 2008-03-28
Thanks for the help...
Solved the problem of libgd but now this is the new output:


In function `GLMaterial::loadTexturePNG(char const*, int, int)':glmaterial.cc:(.text+0x4a8): undefined reference to `gdImageCreateFromPng(_IO_FILE*)'
:glmaterial.cc:(.text+0x50b): undefined reference to `gdImageDestroy(gdImageStruct*)'
:glmaterial.cc:(.text+0x55e): undefined reference to `gdImageGetPixel(gdImageStruct*, int, int)'
:glmaterial.cc:(.text+0x630): undefined reference to `gdImageDestroy(gdImageStruct*)'
collect2: ld returned 1 exit status
make: *** [serpent] Error 1


I checked and libpng12-dev is already installed.

Any solutions?

---

### Post by paolo.komninidis on 2008-03-28
uppp

---

### Post by ubuntogenius on 2008-03-28
Probably it was the wrong library. Try to install newer ones or other ones..

---

### Post by paolo.komninidis on 2008-03-28
i have installed the latest releases of those libraries.
What do you mean other ones?Which?

Can you be more precise?

---

### Post by lloyd_b on 2008-03-28
> **paolo.komninidis said:**
> Thanks for the help...
Solved the problem of libgd but now this is the new output:


In function `GLMaterial::loadTexturePNG(char const*, int, int)':glmaterial.cc:(.text+0x4a8): undefined reference to `gdImageCreateFromPng(_IO_FILE*)'
:glmaterial.cc:(.text+0x50b): undefined reference to `gdImageDestroy(gdImageStruct*)'
:glmaterial.cc:(.text+0x55e): undefined reference to `gdImageGetPixel(gdImageStruct*, int, int)'
:glmaterial.cc:(.text+0x630): undefined reference to `gdImageDestroy(gdImageStruct*)'
collect2: ld returned 1 exit status
make: *** [serpent] Error 1


I checked and libpng12-dev is already installed.

Any solutions?

The problem is with libgd.  Specifically, "glmaterial.cc" is calling some functions that it thinks should be in the libgd library, but which apparently aren't.

Question: which version of libgd did you wind up installing?  The "xpm" or "noxpm" version?  Try installing the *other* one (it should automatically uninstall the first when you do so) and see if those functions are defined in there.

Other than that, I have no clue.  I would suggest marking this thread as solved (go to "Thread Tools" to do so), and then opening up a new thread under a title like "libgd installed, but compiler can't find some gd functions".  Since the title of this thread no longer matches the problem being discussed, it's less likely that somebody familiar with libgd is going to read it...

Lloyd B.

---

### Post by paolo.komninidis on 2008-03-29
ok i will do that


thanks a lot

---

