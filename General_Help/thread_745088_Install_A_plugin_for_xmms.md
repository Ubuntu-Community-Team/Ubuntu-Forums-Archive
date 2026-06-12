---
title: "Install A plugin for xmms"
date: 2008-04-04
forum: General Help
---

### Post by Kerosh on 2008-04-04
Can someone please tell me where to write this code    
    $ ./configure
    $ make
    $ make install
it tells me in the readme to write it in the directory ... but that dosent help me to much ive tried writein it in the adress bar but nothing. I also tried it in the terminal but it kept saying configure aint a directory.
I just need a quick answer thanks

---

### Post by y-lee on 2008-04-04
Open a terminal, cd to the directory that contains the readme file and then type the three separate lines of code below:

```
./configure
make
make install
```

Note: to cd to to the directory use

```

cd directory-path
```


where directory path is the path to the directory in question. If you need more help with this or get a bunch of errors post back. Note build-essentials must be installed to compile (ie make and make install) programs. You can install this in synaptic if it is not already installed.

---

### Post by Kerosh on 2008-04-04
kerosh@kerosh-desktop:~$ cd/home/kerosh/Desktop/xmms-infopipe-1.3
bash: cd/home/kerosh/Desktop/xmms-infopipe-1.3: No such file or directory
kerosh@kerosh-desktop:~$ cd /home/kerosh/Desktop/xmms-infopipe-1.3
kerosh@kerosh-desktop:~/Desktop/xmms-infopipe-1.3$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking how to run the C preprocessor... gcc -E
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependant libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: You need glib 1.2 or later to build this plug-in.
kerosh@kerosh-desktop:~/Desktop/xmms-infopipe-1.3$ make
make: *** No targets specified and no makefile found. Stop.
kerosh@kerosh-desktop:~/Desktop/xmms-infopipe-1.3$ make install
make: *** No rule to make target `install'. Stop.
kerosh@kerosh-desktop:~/Desktop/xmms-infopipe-1.3$ 

sorry mate i dont no how to put it in that box like you do but thats the errors it gave me

---

### Post by y-lee on 2008-04-04
Ok we have some missing dependencies I see, but for future reference:

> sorry mate i dont no how to put it in that box like you do but thats the errors it gave me

The box we use here to put code in is the **# **button on the menu of this text input area. Took me a while to find it myself when I furst starting posting here, I just used the **code** tags till i figured it out.:)

Anyway open synaptic package manager and search for and install  the following packages

[LIST]
[*]autoconf

[*]automake

[*]texinfo
[/LIST]

I don't know what version of Ubuntu you are using but you may have  several different versions of some these and I am not sure which you need to install. It might be wise to install the latest, tho on my machine I have all this installed but not always the latest...just noticed lol. Also you can also search for autoheader, when i do it only shows the package autoconf2.13 ... you probably will have similar results tho maybe a different version ...install it. In situations like this unless i have information on which package i need I install everything related. You may also need autotools-dev installed.

After doing this try again. If ./configure spits out errors post back, no need to try make and make install, it will not work until the config script works correctly with no errors.

Also note dependencies errors can be hard to figure out (for me at least), so good luck and don't be discouraged.

---

### Post by y-lee on 2008-04-04
I just noticed but you should be able to install xmms-infopipe from synaptic, it is in the repos and synaptic should handle the dependencies for you. Plus this method has the advantage of updating when updates come out. I would advise that instead of compiling the source code :)

---

### Post by Kerosh on 2008-04-04
seems very hard just for installing a plugin lol im not used to linux so thats probably why but im geting used to it.
```
kerosh@kerosh-desktop:~$ cd /home/kerosh/Desktop/xmms-infopipe-1.3
kerosh@kerosh-desktop:~/Desktop/xmms-infopipe-1.3$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking how to run the C preprocessor... gcc -E
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependant libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: You need glib 1.2 or later to build this plug-in.
kerosh@kerosh-desktop:~/Desktop/xmms-infopipe-1.3$ make
make: *** No targets specified and no makefile found. Stop.
kerosh@kerosh-desktop:~/Desktop/xmms-infopipe-1.3$ make install
make: *** No rule to make target `install'. Stop.

```

i downloaded everything you told me to seems to of found more thnigs but still isnt working. Any more tips ?

---

### Post by Kerosh on 2008-04-04
could you give me a step by step guide on how to do that ? thanks :)

---

### Post by Kerosh on 2008-04-04
ive done it thanks alot :)

---

### Post by y-lee on 2008-04-04
Try 

```
sudo apt-get install xmms-infopipe-1.3
```

Or open synaptic and search for xmms-infopipe and install it there.

If you would rather compile it you are now missing libglib and libglib-dev, find those in synaptic and install. And try to compile again.

Edit just saw your new post.

---

### Post by y-lee on 2008-04-04
> i've done it thanks alot 

No problem glad I could help and thanks for the thanks. I love watching my  thanks count go up. :lolflag:

Edit: You can also mark this as solve if everything is working for you, click on thread tools above. Helps make the forums easier to use for those of us helping alot here :)

---

