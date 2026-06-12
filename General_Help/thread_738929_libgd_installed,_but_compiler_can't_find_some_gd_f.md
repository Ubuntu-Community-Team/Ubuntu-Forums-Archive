---
title: "libgd installed, but compiler can't find some gd functions"
date: 2008-03-29
forum: General Help
---

### Post by paolo.komninidis on 2008-03-29
I am trying to compile a program i wrote in C++ with opengl.

when i try to compile......this is the output:

In function `GLMaterial::loadTexturePNG(char const*, int, int)':glmaterial.cc.text+0x4a: undefined reference to `gdImageCreateFromPng(_IO_FILE*)'
:glmaterial.cc.text+0x50b): undefined reference to `gdImageDestroy(gdImageStruct*)'
:glmaterial.cc.text+0x55e): undefined reference to `gdImageGetPixel(gdImageStruct*, int, int)'
:glmaterial.cc.text+0x630): undefined reference to `gdImageDestroy(gdImageStruct*)'
collect2: ld returned 1 exit status
make: *** [serpent] Error 1


I have tried to install both libgd-xpm and -noxpm. But i got the same errors.

This is my Makefile:


CPP = g++ -g
CC = gcc
OBJ = main.o serpent.o mondo.o punto.o globject.o alimento.o ostacolo.o glmaterial.o auxiliar.o model.o alcool.o display.o
LINKOBJ = ${OBJ}
LGD = -lgd -lpng -lz -ljpeg -lfreetype -lm
LIBS = -L/usr/X11R6/lib -L/tmp/usr/lib -lGL -lGLU -lglut $(LGD)
INCS = -I/usr/X11R6/include -I/tmp/usr/include
BIN = serpent
CFLAGS = $(INCS) -Wall
CXXFLAGS = $(CFLAGS) $(EXTRA)
RM = rm -f

.PHONY: all all-before all-after clean clean-custom

all: all-before $(BIN) all-after

clean: clean-custom

${RM} $(OBJ) $(BIN)

$(BIN): $(OBJ)


Do you have any solutions?
Thank you

$(CPP) $(LINKOBJ) -o $(BIN) $(LIBS)

---

### Post by paolo.komninidis on 2008-03-29
uppp

---

### Post by paolo.komninidis on 2008-03-29
noone can give a solution to my problem?
it is important.i need this qorking for a project i have to do for the university....
please

---

### Post by Petrock6 on 2008-03-29
Are you trying to make a GUI?

---

### Post by paolo.komninidis on 2008-03-30
No. It's only an OpenGL game written in C++. And i cannot understand why it gives me that errors. The library is installed but it cannot find thosw functions

---

