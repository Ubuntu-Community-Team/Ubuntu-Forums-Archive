---
title: "make ** no targets specified and no makefile found. stop // bash: ./configure: No suc"
date: 2018-08-14
forum: General Help
---

### Post by frankyfrodo on 2018-08-14
Hi everyone,
I am new at this community and new at Lubuntu. I must say that I have already successfully installed a bunch of softwares, but now I am struggling with an issue I can't solve. 
I have read the comments on this post below
[https://stackoverflow.com/questions/14412919/make-no-targets-specified-and-no-makefile-found-stop](https://stackoverflow.com/questions/14412919/make-no-targets-specified-and-no-makefile-found-stop)
, but I can't still not solve the problem.

I am trying to install the sotware CVAssistant, that I have found here:

[https://sourceforge.net/projects/cvassistant/](https://sourceforge.net/projects/cvassistant/)

the INSTALL file on which I am referencing is here:

[https://sourceforge.net/p/cvassistant/code/ci/master/tree/](https://sourceforge.net/p/cvassistant/code/ci/master/tree/))

I have successfully installed qt5:

-----------------------
Extract of the INSTALL
-----------------------
For instance to install dependencies under debian jessie:
    sudo apt-get update
    sudo apt-get install qt4-qmake libqt4-dev libquazip-dev

and for debian with qt version 5:
    sudo apt-get update
    sudo apt-get install qt5-qmake libqt5-dev libquazip-qt5-dev
-----------------------
But when I follow the instructions of the INSTALL file I can't compiled the file part that says:

------------------------
Extract of the INSTALL
-----------------------Finally to build it:
    tar -xf ./cvassistant-<version number here>.tar.bz2
    cd ./CVAssistant
    qmake
    make
---------------

When I type Make command it shows:
make ** no targets specified and no makefile found. stop 


On the other discussion on the topic a guy said to run ./configure, but when I type this command it shows:
 bash: ./configure: No such file or directory

Can Anyone help me please?

---

### Post by wyliecoyoteuk on 2018-08-14
Are you in the correct build directory?
what is the output from:
```
pwd
```

Note that the directory name is case sensitive. ./CVAssistant is not the same as ./cvassistant, and is almost certainly a typo in the install guide.

---

### Post by frankyfrodo on 2018-08-14
thanks for your answer!

This is the result of pwd:
/home/anam/Downloads/CVAssistant

I use Lubuntu 18.04 version.

---

### Post by frankyfrodo on 2018-08-14
This is te name of the file that I correctly unzip after download:
cvassistant-3.1.0-linux-amd64.tar.bz2

renaming the file as:

CVAssistant

---

### Post by steeldriver on 2018-08-14
`no makefile found` suggests that the previous `qmake` command did not complete successfully - run it again, and check carefully for any error messages

---

### Post by frankyfrodo on 2018-08-14
Yes you are right.
This is the message that shows up when I try to run the command qmake 

anam@anam-Aspire-E3-111:~/Downloads/CVAssistant$ qmake

where  CVAssistant is the unzip folder

----------------------
message
---------------------

Usage: /usr/lib/x86_64-linux-gnu/qt4/bin/qmake [mode] [options] [files]

QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

---

### Post by steeldriver on 2018-08-14
I just checked on sourceforge, and it looks like cvassistant-3.1.0-linux-amd64.tar.bz2 actually contains a pre-built binary version of the program rather than a source tarball - are you sure the instructions you are following are appropriate?

---

### Post by oldos2er on 2018-08-14
Thread moved to General Help.

---

### Post by frankyfrodo on 2018-08-17
I am sorry for the question I am going to ask you but:

What does a pre-built binary version do? Is it a executable file?

Cause one thing I have understood is that the qmake command build an executable file from a source file, in my case wrote in C++.
I have been reading the pages at the links that oldos2er posted. They are really interesting, most of all the first one.
Yesterday I tried to study a bit the qmake command. I will follow trying to figure it out how to give the qmake command work and I'll make you know. 

Thanks for your support

---

### Post by steeldriver on 2018-08-17
As far as I can see, the archive contains the following

```

bin  CVAssistant.desktop  lib  licence.txt  README  run

```

You can run the application directly from that location by typing

```

./run

```

(`run` is just a script that sets a qt plugin path and then calls the binary executable).

---

