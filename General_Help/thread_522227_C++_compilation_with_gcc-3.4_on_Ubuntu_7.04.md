---
title: "C++ compilation with gcc-3.4 on Ubuntu 7.04"
date: 2007-08-10
forum: General Help
---

### Post by vae on 2007-08-10
I am trying to compile C++ programs with gcc-3.4 on Ubuntu 7.04 and i get following error:

[FONT="Courier New"]*gcc-3.4: installation problem, cannot exec `cc1plus': No such file or directory*[/FONT]

I tried to re-install gcc-3.4 but it's same again.
Is there a problem with gcc-3.4 package?

//Ilija

---

### Post by LaRoza on 2007-08-10
Run this command:

```

sudo aptitude install build-essential

```

This will get everything you need for compiling c/c++.

To compile a C++ file, named hw.cpp, navigate to its directory do one of the following:

```

g++ hw.cpp

g++ hw.cpp -o hw.bin

g++ -c hw.cpp

```

The three command do different things. The first compiles it and links it and makes an executable file named "a.out".

The second does the same but names the resulting program is names hw.bin, you don't need a file extension, but I usually use them.

The third doesn't link the program and generates a .o file.

---

### Post by hairyhi on 2007-08-10
hey i have a problem with gcc.

I need a code to run gcc to compile a code and then run it while taking input from a text file and put output to a text file. Also I need to fix some runtime for the execution. I mean if a program goes in an infinite loop, then I m able to exit the program automatically without any difficulty.

---

### Post by vae on 2007-08-10
I have allready installed build-essentias, but it concerns current gcc version 4.1.2.
I don't have problem compiling C++ with gcc 4.1.2 but with gcc 3.4. And for some reason i have to use gcc 3.4

---

### Post by ichigo on 2007-09-19
Had the same prob with gcc-4.2. Installing

gcc-4.2 libdb4.2++c2

solved the problem for me. Guess that there are similar ones for gcc-3.4

---

