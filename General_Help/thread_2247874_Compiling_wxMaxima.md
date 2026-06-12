---
title: "Compiling wxMaxima"
date: 2014-10-11
forum: General Help
---

### Post by linux_dream on 2014-10-11
Hi guys,
I'm having troubles compiling wxMaxima. I've read that I need the wxwidgets ([http://www.wxwidgets.org/](http://www.wxwidgets.org/)), so I downloaded the source files for linux, compiled them (took around 30 minutes) and then installed them.
After this, I downloaded wxMaxima's source files on sourceforge and then followed wxMaxima's readme file to compile it:
```
If you are building from git, execute `./bootstrap` first.

To build wxMaxima on Linux execute

    ./configure
    make
    cd locales
    make allmo
    cd ..
    sudo make install
```
Here's what I tried: 
```
isaac@isaac-desktop:~/Downloads/wxmaxima-code-ada5844b3d800e332b843d058a7c699752f7c26e$ ./bootstrap 
configure.ac:14: warning: macro 'AM_OPTIONS_WXCONFIG' not found in library
configure.ac:99: warning: macro 'AM_PATH_WXCONFIG' not found in library
configure.ac:11: installing './config.guess'
configure.ac:11: installing './config.sub'
configure.ac:6: installing './install-sh'
configure.ac:6: installing './missing'
src/Makefile.am: installing './depcomp'
configure.ac:14: error: possibly undefined macro: AM_OPTIONS_WXCONFIG
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:99: error: possibly undefined macro: AM_PATH_WXCONFIG


isaac@isaac-desktop:~/Downloads/wxmaxima-code-ada5844b3d800e332b843d058a7c699752f7c26e$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
./configure: line 2642: AM_OPTIONS_WXCONFIG: command not found
checking whether make sets $(MAKE)... (cached) yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
./configure: line 3606: syntax error near unexpected token `2.8.4,'
./configure: line 3606: `AM_PATH_WXCONFIG(2.8.4, wxWin=1, wxWin=0, xml,html,adv,aui,core,net,base)'
isaac@isaac-desktop:~/Downloads/wxmaxima-code-ada5844b3d800e332b843d058a7c699752f7c26e$ make
make: *** No targets specified and no makefile found.  Stop.



```
Then I cd to locales and of course "make allmo" does not work, there is no such target because of the error(s) above.
Any help is appreciated... 
Thanks in advance.

---

### Post by steeldriver on 2014-10-11
Did you try using the pre-built version from the repository? it will be a lot easier than building from source - or if you need a newer version of wxMaxima, at least use the pre-built version of the underlying wxwidgets development package (FWIW I was able to build wxmaxima-14.09.0 from the tarball on my 12.04  box after installing libwxgtk2.8-dev from the repo)

You probably should not have run ./bootstrap since you are building from a tarball not directly from the git repository - I don't know if that will have made any difference though

---

### Post by linux_dream on 2014-10-11
> **steeldriver said:**
> Did you try using the pre-built version from the repository? it will be a lot easier than building from source - or if you need a newer version of wxMaxima, at least use the pre-built version of the underlying wxwidgets development package (FWIW I was able to build wxmaxima-14.09.0 from the tarball on my 12.04  box after installing libwxgtk2.8-dev from the repo)

You probably should not have run ./bootstrap since you are building from a tarball not directly from the git repository - I don't know if that will have made any difference though

First of all thank you very much for the reply!
In fact I don't need a newer version than the one in the repository. I needed a newer version of Maxima which I successfully compiled and installed. However if I try to install wxMaxima from the Lubuntu software center, it wants to install a few packages (dependencies) but Maxima (older version than mine) is listed... And I don't know how to install all packages but Maxima's since I already have it installed.

_**EDIT**_ : I installed wxMaxima in the repository, even though it installed an old version of Maxima. When I run wxMaxima, it's using the latest dev. version, so problem solved :)

---

