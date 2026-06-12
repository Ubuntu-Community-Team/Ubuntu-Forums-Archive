---
title: "install svn aMSN"
date: 2008-06-02
forum: General Help
---

### Post by rxbandit on 2008-06-02
I get an error when i try and use my mic and webcam on my Dell Vostro 1400. Webcam works but no audio thru mic. So I'm trying to update to latest svn of aMSN.Hopefully someone has solution, google was no help.

 ```
brian@Vostro:~/amsn$ ./configure
checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib
checking for main in -lstdc++... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for png_read_info in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for jpeg_CreateDecompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking jerror.h usability... yes
checking jerror.h presence... yes
checking for jerror.h... yes
checking for ftello... yes
checking for fseeko... yes
checking for getpt... yes
checking for strcasestr... yes
checking for memmem... yes
checking for dlopen... no
checking for pthread_create in -lpthread... yes
checking if mmx should be used... no
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GST... yes
checking for FARSIGHT2... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/linux/capture/config.h
config.status: utils/linux/capture/config.h is unchanged

compile time options summary
============================

    X11          : yes
    Tcl		 : 8.4
    TK 		 : 8.5
    DEBUG        : no
    STATIC       : no
    FARSIGHT     : yes

brian@Vostro:~/amsn$ sudo make
[sudo] password for brian: 
  CXX	  utils/TkCximage/src/TkCximage.cpp.o
In file included from utils/TkCximage/src/TkCximage.h:21,
                 from utils/TkCximage/src/TkCximage.cpp:11:
/usr/include/tcl8.5/tk.h:23:3: error: #error Tk 8.5 must be compiled with tcl.h from Tcl 8.5
make: *** [utils/TkCximage/src/TkCximage.cpp.o] Error 1
brian@Vostro:~/amsn$ 

```

---

### Post by andrew.46 on 2008-06-02
Hi,

I suspect that you are missing the relevant dev file. Try the following:

```
$ sudo apt-get install tcl8.5-dev tk8.5-dev 
```

and recompile.

    Andrew

---

### Post by rxbandit on 2008-06-02
Nope I have both of those installed. Thanks though.

---

### Post by Claus7 on 2008-06-02
Hello,

you might have both of them, yet tcl 8.5 is not recognised by amsn svn during compilation. So you should compile amsn with the right arguments for the tcl library. 
See also my script :
[http://ubuntuforums.org/showthread.php?t=712425](http://ubuntuforums.org/showthread.php?t=712425)

Regards!

---

