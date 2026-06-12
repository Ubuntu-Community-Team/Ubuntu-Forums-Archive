---
title: "Supertux /CVS/Aclocal --&gt; Problem!"
date: 2004-11-25
forum: General Help
---

### Post by ankitmalik on 2004-11-25
Hi

Since this is my first thread on this forum, I shall have to begin with 'UBUNTU ROCKS and it clearly ROCKS atleast for me.'

Coming to the main point! I was just trying to install Supertux from the CVS. So as per the site's instruction I downloaded (I am not sure whether download is the correct word here, since I am completely new to CVS, so plz. pardon me if it is wrong) 

From what I see in the INSTALL file in the supertux folder, I have to do

# sh autogen.sh

And so I did, and it gave a few errors.

They mostly pertained to a few commands not being found namely

a) autoconf            b) autoheader         c) aclocal

With my limited knowledge, I guessed out that I need to install these.

So I did it an apt-get install autoconf and I had the package installed.

I did an apt.... for b) but it said package not found! Ditto for c)

Now I tried 
# sh autogen.sh again

The error now goes as follows

"# sh autogen.sh
autogen.sh: line 10: aclocal: command not found
"

So what do I do? Which package should I install?

Soliciting solution for the above because I really love playing Supertuxido..... ! [aka Supertux]

Thanks in advance.

---

### Post by astoltz on 2004-11-25
Supertux is in the universe repository so if you haven't enabled it you'll have to add it to your /etc/apt/sources.lst.  Then it's as easy as:

sudo apt-get update
sudo apt-get install supertux

---

### Post by ankitmalik on 2004-11-25
Oops.. I am really sorry for not mentioning one thing!

I already have Supertux from the Ubuntu Repository.

But I want the Bleeding Edge CVS Version.

And so I need the workaround for the CVS version.

But Thanks anyways!

More help solicited! :D

---

### Post by piedamaro on 2004-11-25
You need aclocal (as well as many other tools, probably). It should be in the automake package.

---

### Post by ankitmalik on 2004-11-25
Thanks for the automake tip.

The autogen.sh for supertux finally worked!

So it created a 'configure' file

Now the problem is with configure  :-o 

The error is as follows
```
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.4 not found!
``` 


This is the error bit. The full listing is as follows >

>>>
root@tuxido:/home/maliks/supertux # ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for gprof mode... disabled
checking for debug mode... disabled
checking wether OpenGL should be used... yes
checking for iconv_open in -liconv... no
checking for sdl-config... no
checking for SDL - version >= 1.2.4... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.4 not found!
>>>

---

