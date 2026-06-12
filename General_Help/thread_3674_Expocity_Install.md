---
title: "Expocity Install"
date: 2004-11-08
forum: General Help
---

### Post by jdusablon on 2004-11-08
Anyone have any success installing Expocity? I've tried and get:```
# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.27.2 found
checking for perl... /usr/bin/perl
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for char... yes
checking size of char... 1
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for int... yes
checking size of int... 4
checking for void *... yes
checking size of void *... 4
checking for long long... yes
checking size of long long... 8
checking for __int64... no
checking size of __int64... 0
checking whether byte ordering is bigendian... no
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking for backtrace... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  am ar az be bg bn ca cs cy da de el en_GB es fa fi fr ga gl he hi hu id is it ja ko lt lv mk ml mn ms nl nn no pl pt pt_BR ro ru sl sk sq sr sr@Latn sv ta tr uk vi wa zh_CN zh_TW
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.2.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```I did have to install a few things...g77, g++, etc. I'm kind of stuck now.

Anyone? This would really help me learn to install other non-apt-get things. Apt-get spoils a person.

---

### Post by az on 2004-11-08
apt-get install build-essential

also, you need library development files like libgtk2.0-dev.  That depends on what you want to build.  It is usually mentioned in the readme.

---

### Post by jdusablon on 2004-11-08
Hmmmm.... Did those things, still same error. What is the file equivalent to **gtk+-2.0.pc** in a standard Ubuntu setup?

---

### Post by adamvert on 2004-11-08
[QUOTE=jdusablon]Hmmmm.... Did those things, still same error. What is the file equivalent to **gtk+-2.0.pc** in a standard Ubuntu setup?[/QUOTE]
 If I can just jump in here with an abstracted question... :)

Why is it that some packages add pkg-config files, and others don't?  And how do you deal with it when you're trying to compile something that depends on a package that you *know* you have, but you somehow don't have the .pc file for?

ta!
Adam

---

### Post by jdusablon on 2004-11-08
Another good question is: for extremely high-demand software like **expocity**, why on earth is there no .deb package for it, let alone an apt-get repository package??

For those who are wondering what expocity is, it is a metacity patch that allows users to switch windows in a fashion similar to Expose in OSX Panther.

---

### Post by Roland77 on 2004-12-17
I guess all that software is still beta-stage, ( skippy / kompose / expocity ) there is no distro that includes those.
I once found rpm's of Skippy for red hat / fedora; that's it. Seems 2 me we just need to learn the compiling stuff ;) 

 So far I got the same errors u had Jdusablon, but adding the development tools worked; I came a little further this time ^^

The process stopped at this:
QUOTE:
configure: error: Library requirements (gtk+-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
END QUOTE.

I've read on these boards some people managed to get it installed, could anyone help ?
I'm really trying to get rid of M$-stuff; I want to only run linux on my thinkpad, I just got sick of all the spyware / virusses / u name it... Thought I'd rather spent all my time learning this OS then fixing BS on windows, lol. I got all software I needed sofar, to get to work etc, now it's time for the eye-candy part ;)
I tried compiling skippy too, I guess I just like Expose :)
If anyone has a tip or a guide plz post here !
(BTW Sorry in advance for the n00bish questions :P )

gr.Roland

---

### Post by meznak on 2005-07-29
I have the same problem on my system... was this ever resolved?  If so, how?

---

### Post by H.E. Pennypacker on 2006-06-21
> Another good question is: for extremely high-demand software like expocity, why on earth is there no .deb package for it, let alone an apt-get repository package??

Such a good question.  After having to run around downloading this and that because the terminal was giving me millions of errors, I gave up.  Expocity is simply not worth all the trouble.  Why make users go through all the loopholes, having to download all sorts of files here and there, having to type in cryptic commands, and more just to use something as simple as Expocity?

You should be able to download a single file that will, if necessary, download anything else it needs.  Don't bother me telling me I don't have such and such dependencies.  If I don't, why not just download it, and STOP TELLING ME.  Double-click on that file and something will automatically take care of it.

There should be something like a wizard that will take you through several steps in order to install software instead of adding commands to the terminal (I am not talking about stuff that is already in Synaptic).  Something like this:

[img]http://www.digitalmapping.sk.ca/pop3srv/images/installer.JPG[/img]

Or

[img]http://fedora.redhat.com/projects/anaconda-installer/images/screenshot-0003.png[/img]

---

### Post by H.E. Pennypacker on 2006-06-21
[QUOTE=meznak]I have the same problem on my system... was this ever resolved?  If so, how?[/QUOTE]

I am at the GTK error step too.  I can't get past it.  I figured I didn't have gtk+-2.0, so I looked it up in Synaptic.  Couldn't find it there, so I went to gtk+-'s official website, and after downloading it, I tried to install gtk+-2.0.  That didn't work for the same reason as Expocity: gtk+-2.0 wasn't installed, so I couldn't install gtk+-2.0.  So, in short, I'd first need to install gtk+-2.0, before I could install gtk+-2.0.  If it sounds confusing, it's because it *is* confusing.

---

### Post by hizaguchi on 2006-09-12
For the gtk error, did you try installing the gtk dev packages?  That's often necessary for compiling software.

As for the point and click compiling idea, that has some serious problems.  Sure, it'll *seem* easier for people who are unwilling to use the command line, but what happens when the system is unable to resolve a dependency?  Or a compile error occurs?  A GUI is not flexible enough to deal with all the possible problems that could go wrong at compile time.  You don't get the feedback you need to solve the problem.  I'll take a powerful and flexible interface over a pretty one any day.

---

