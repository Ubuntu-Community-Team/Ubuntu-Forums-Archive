---
title: "How to get QT4 compilation working under ubuntu"
date: 2006-09-27
forum: General Help
---

### Post by ephie on 2006-09-27
Hello everybody,

I'm trying to get the Qt4 package installed on Dapper Drake Ubuntu.

I installed all the packages that started with qt (qt4-designer and so on...) and then i tryed to compile my hello.cpp file...

What I did:

Fisrt I cd to ~/hello directory
then I did a qmake -project that created a hello.pro file
then a qmake hello.pro that created a make file
then a make.... and that only created a hello.o file.... 

the hello.o file is not an executable file.. something went wrong! But what....


In my first attemps I didn't have gcc and g++ installed so I didn't even get that far. Maybe there are some other packages that have to be installed but I have no idea which ones!!!!

Can someone help me on this question??

I'd be realy thankfull... I spend so much time on this problem already.... (I got the compilation going under windows.... but I'd far rather program under Ubuntu!!:D )

Thanks guys

---

### Post by Leeghoofd on 2006-09-27
it appears i have a simular problem:

checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!

Qt was installed through synaptic, but it does not seem to be functioning properly. If anyone has an idea please feel free to mention it here](*,)

---

### Post by ephie on 2006-10-30
hi,

If you have the same problem I had, you will have to install the

libqt4-debug and the libqt4-debug-dev packages through synaptic or through a prompt: 

sudo apt-get install libqt4-debug

sudo apt-get install liqt4-debug-dev

have a go,

eph!e

---

