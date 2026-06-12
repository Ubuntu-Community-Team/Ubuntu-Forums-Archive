---
title: "adesklets"
date: 2005-04-04
forum: General Help
---

### Post by flow on 2005-04-04
im trying to install adesklets..
adesklets.sf.net
but i got the following error.

 ./configure --with-           python-force-detection
checking for a BSD-compatible install... /usr/bin/insta           ll -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.o           ut
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (ca           ched) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
configure: WARNING:
-----------------------------------------------------
`flex' was not found on your system. If you encounter
problems recompiling a `l' file, please try `flex'
first. You can get it from any GNU archive site.
You will not need `flex' as long as you do not
modify `l' files.
----------------------------------------------------
checking for bison... no
checking for byacc... no
configure: WARNING:
-----------------------------------------------------
Nor `byacc' or `yacc' parsers had been used
for developing adesklets. If you encounter problems
recompiling a `y' file, please try `bison' instead.
You can get it from any GNU archive site. You will
not need `bison' as long as you do not modify
`y' files.
-----------------------------------------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
**checking for Python include path... find: /usr/include/python/: No such file or directory**

**configure: error: cannot find Python include path**


how do i resolve this?

---

### Post by Leif on 2005-04-04
That's because the directory is actually /usr/include/python2.4/
 (or 2.3) depending on your system. If you don't want to go and play with the makefiles, a deb package for adesklets exists at :

    deb [http://themind.altervista.org/debian](http://themind.altervista.org/debian) unstable main
    deb-src [http://themind.altervista.org/debian](http://themind.altervista.org/debian) unstable main 

Keep in mind these are debian packages, NOT ubuntu, so they may cause problems, and since I haven't tried to install them myself, I can't vouch for them.

---

### Post by flow on 2005-04-05
[QUOTE=Leif]That's because the directory is actually /usr/include/python2.4/
 (or 2.3) depending on your system. If you don't want to go and play with the makefiles, a deb package for adesklets exists at :

    deb [http://themind.altervista.org/debian](http://themind.altervista.org/debian) unstable main
    deb-src [http://themind.altervista.org/debian](http://themind.altervista.org/debian) unstable main 

Keep in mind these are debian packages, NOT ubuntu, so they may cause problems, and since I haven't tried to install them myself, I can't vouch for them.[/QUOTE]


i tried creating a symlink to /usr/include/python ,but that didnt work as well.

---

### Post by seph on 2005-04-26
I too am having this same problem with the path to python while installing adesklets.  Has anybody found a solution yet?

---

### Post by lgavinho on 2005-05-06
You need to install python-dev_2.4.1-0ubuntu2_all.deb and python2.4-dev_2.4.1-0_i386.deb to resolve python include.
But I can't install, because another problem :-? :

configure: error: Could not find terminal management library for readline
(either ncurses, termcap or curses).

---

### Post by mike998 on 2005-07-14
I'm trying now and have the same problem with not finding a terminal management library...
Did you manage to solve this?

EDIT: I solved it myself - I installed libreadline5-dev, and libimlib2-dev

---

