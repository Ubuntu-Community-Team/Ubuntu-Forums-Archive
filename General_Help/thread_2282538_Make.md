---
title: "Make"
date: 2015-06-15
forum: General Help
---

### Post by Miykel on 2015-06-15
G'Day I'm trying to install libdvdcss-1.2.13.tar.bz2

cp to usr/src, extracted with terminal then followed install.txt 


INSTALL file for libdvdcss, a DVD access library


Configuring libdvdcss
=====================

A typical way to configure libdvdcss is:

   ./configure --prefix=/usr

See `./configure --help' for more information.


If you got libdvdcss from its version control system, please bootstrap first:

   autoreconf -i


Building libdvdcss
==================

Once configured, run `make' to build libdvdcss.

If you have player keys, you need to put them in the file csskeys.h, before
configuring libdvdcss to enable the "key" method (the one from libcss).


Installing libdvdcss
====================

You can install libdvdcss by typing:

   make install

But when I get to make i get  

root@miykel:/home/miykel# cd /usr/src/libdvdcss-1.2.13/
root@miykel:/usr/src/libdvdcss-1.2.13# make
make: *** No targets specified and no makefile found.  Stop.
root@miykel:/usr/src/libdvdcss-1.2.13# 

but there is makefile.am and makefile.is and what targets do I need

Regards Miykel

---

### Post by Holger_Gehrke on 2015-06-15
You need to configure it before you can make it. One of the things '/.configure' does is to generate a 'Makefile' from 'makefile.am' / 'makefile.in'.

---

### Post by Miykel on 2015-06-15
Thanks for the reply  				 				 					 						 	[**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("http://ubuntuforums.org/member.php?u=1961578"), I just checked and no it didn't, no makefile...should I run the .configure again ??

---

### Post by Miykel on 2015-06-15
[**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("http://ubuntuforums.org/member.php?u=1961578") I just noticed the way you wrote the configure command and I do believe I wrote it wrong in the terminal, ie. /configure instead of ./configure, no dot....so easy to make a mistake, all adds to the learning curve I guess
Many thanks again, your help is appreciated.
Regards M

---

### Post by Holger_Gehrke on 2015-06-15
I re-read your original post a bit more careful and there's one thing I don't understand: why did you copy and unpack the source-code in /usr/src ? That's a system directory that holds the kernel header files ... To copy and extract your archive there you probably had to use sudo; if you didn't use sudo with configure, then it probably couldn't write the Makefile ...

When I build stuff from source, I unpack into a directory in my home-directory. Remove the unpacked files from /usr/src and try it like this:
```

mkdir ~/src
cd ~/src
tar -xjf path/to/downloaded/libdvdcss-1.2.13.tar.bz2

```
The last step should create a directory full of source code. Change into that directory then do
```

./configure && make && make install

```

(it should have been '**./**configure' in my previous post, too. '.' -- the current directory -- is normally not in $PATH, so you have to give it when calling scripts or programs located there)

---

### Post by raja.genupula on 2015-06-15
make sure , make install either you are executing as sudo or sudo make install

---

### Post by ajgreeny on 2015-06-15
Just a query; why install from source when you can do it from a script included in **libdvdread4** which you can install from repos?

Perhaps you want to do this as a simple(?) exercise in compiling a package?

---

