---
title: "installing aMSN with webcam support?"
date: 2005-09-19
forum: General Help
---

### Post by cristianommxp on 2005-09-19
Hi, I tryed to install aMSN from CVS to start webcam support on my Linux.

My webcams is working fine. It's working fine with other communicators, like Qnext. 

But I want to chat with friends that use MSN communicator. Only aMSN has support to webcam. So I need to install it.

Well. I have tryed do install aMSN with this steps:

1 $ wget [http://amsn.sourceforge.net/amsn_cvs.tar.gz](http://amsn.sourceforge.net/amsn_cvs.tar.gz) .
2 $ sudo tar zxf amsn_cvs.tar.gz -C /opt
3 $ sudo chown cris:root -R /opt/msn
4 $ cd /opt/msn
5 $ /.configure
6 $ make
7 $ ./amsn

The process works fine until stap 5, when I have a problem:

-------------------------------------------------------------------------------------------------
$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... configure: error: Unable to find Tcl
directory or Tcl package is not tcl-dev
-------------------------------------------------------------------------------------------------

The "configure" script in the aMSN directory needs a "TCL" package. 

1) What package is it talking about? 
2) Whats TCL? 
3) Whats the function of TCL package? 
4) How can I install TCL package? 
5) Whats the name of TCL package in the Ubuntu's repository ?


10ks.


Cristiano

---

### Post by lithorus on 2005-09-19
Try with tcl8.4-dev

TCL stands for "Tool Command Language"

---

### Post by cristianommxp on 2005-09-19
ok, "configure" script now can find TCL.

but now I have another error message:

-----------------------------------------------------------------------------------------------------------
$ ./configure

(... blah blah blah ...)

checking tk build dir... using tk library in /usr/lib
./configure: line 3156: /usr/lib/tkConfig.sh: No such file or directory
-----------------------------------------------------------------------------------------------------------

Whats "TK" ? 
How can I install TK in Ubuntu?
Whats the name of package?


10ks.


Cristiano

---

### Post by lithorus on 2005-09-19
There is a package called tk8.4-dev.

Don't take this the wrong way, but do yourself a favor and learn how to use the search features in either aptitude or synaptic :) Especially if you are going to compile stuff on your own. Reading the README for dependencies also helps.

---

### Post by arunsub on 2005-09-19
After you install it, tell me if you can do video chat with people using Windows based MSN messenger. I tried to do that. After the user accepted my webcam invitation, it said connecting for a long time and said couldn't start webcam. I tried with 2 different people.

---

