---
title: "C in Ubuntu"
date: 2005-03-31
forum: General Help
---

### Post by Sitsuj on 2005-03-31
:?: How can in compile programs, that are written in C, in Ununtu? Which compiler is the best?  I've just started my adventure with Linux.  :?:

---

### Post by lao_V on 2005-03-31
All Linux distros come with gcc/g++ for C/C++. You might want to install the build-essential package to be able to compile/build/install programs on your machine

---

### Post by Sitsuj on 2005-03-31
Thank You very much for Your answer, but could You tell me, where can I find those packages? I mean webpage, FTP, or something like that.

---

### Post by lao_V on 2005-03-31
You can install this package using Synaptic package manager or in the terminal type: sudo apt-get install build-essential.

---

### Post by Nadir on 2005-03-31
[QUOTE=Sitsuj]Thank You very much for Your answer, but could You tell me, where can I find those packages? I mean webpage, FTP, or something like that.[/QUOTE]

Use Ubuntu's synaptic package manager
Or in alternative, from a terminal, run

sudo apt-get update
sudo apt-get install build-essentials

Tristan

---

### Post by Sitsuj on 2005-03-31
Thank You all. I've already installed those packages. But now I don't know how to use them. Could you give me a step-by-step advice, what should I do, to make a program in C?

---

### Post by lao_V on 2005-03-31
Do you want to write your own program or do you want to compile/install software written by others?

---

### Post by az on 2005-03-31
build-essential, not build-essentials.


Most free and open source software is made to be able to compile on _any_ unix platform.  That means that there are tools in place to make your life easier.


Typically, to install something from source you need to:

unpack the compressed file (tarball)

tar xvzf <package>

enter the directory
cd <directory>

Configure the source code to use the ressources available on your system
./configure

Then compile the code.  There is a makefile that holds all the rules to follow for the compiler
make

Then install the application:
make install


Prebuilt packages are available.  They have been compiled and can be easily installed, configured and removed.  While the greatness of open-source software is the ability to make any software on your system, you should use the prebuilt packages when you can (like 99.9 percent of the time)

With the freedom to chose the software that you run comes a lot of variations.  This can be a problem if they conflict with each other.  This is known as dependancy hell and can be avoided by using the package manager.  Debian uses an advanced package manager and Ubuntu is based on Debian.

Good luck.

---

### Post by Sitsuj on 2005-03-31
I just wanted to write my own program, compile & run it. Is that a problem? I've created file named: "xxx.cpp" but what now? How to edit, compile and run it?

---

### Post by lao_V on 2005-03-31
you can edit it in any text editor. to compile it and run it follow [these steps]("http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=33")

alternatively you can use an IDE. For KDE there's Kdevelop, not sure about gnome..maybe gambas?? i'm sure there are plenty out there

---

### Post by Sitsuj on 2005-03-31
Big THX.  [-o<

---

