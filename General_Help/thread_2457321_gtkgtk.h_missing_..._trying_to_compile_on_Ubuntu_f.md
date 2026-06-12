---
title: "gtk/gtk.h missing ... trying to compile on Ubuntu first time"
date: 2021-01-30
forum: General Help
---

### Post by michael351 on 2021-01-30
I decided to build an application from source code to master the steps - this is my first time.
My target is an audio converter (fre:ac) 

I followed these instructions:

```
$ git clone https://github.com/enzo1982/smooth.git
$ cd smooth
$ make
$ sudo make install
$ git clone https://github.com/enzo1982/BoCA/
$ cd BoCA
$ make
$ sudo make install


```

and during the make install (compile) stage it generated this error:

```
mkdir -p ./bin ./lib
cd classes && make  && cd ..
make[1]: Entering directory '/home/local/smooth/classes'
cd backends && make  && cd ..
make[2]: Entering directory '/home/local/smooth/classes/backends'
cd cocoa && make  && cd .. && cd gdiplus && make  && cd ..
make[3]: Entering directory '/home/local/smooth/classes/backends/cocoa'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/local/smooth/classes/backends/cocoa'
make[3]: Entering directory '/home/local/smooth/classes/backends/gdiplus'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/local/smooth/classes/backends/gdiplus'
cd haiku && make  && cd .. && cd win32 && make  && cd ..
make[3]: Entering directory '/home/local/smooth/classes/backends/haiku'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/local/smooth/classes/backends/haiku'
make[3]: Entering directory '/home/local/smooth/classes/backends/win32'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/local/smooth/classes/backends/win32'
cd xlib && make  && cd ..
make[3]: Entering directory '/home/local/smooth/classes/backends/xlib'
Package x11 was not found in the pkg-config search path.
Perhaps you should add the directory containing `x11.pc'
to the PKG_CONFIG_PATH environment variable
No package 'x11' found
Package gtk+-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-3.0' found
g++ -I"/home/local/smooth/classes/backends/xlib"/../../../include   -fvisibility=hidden -fPIC -pthread -DSMOOTH_DLL  -c backendxlib.cpp -o backendxlib.o
backendxlib.cpp:11:10: fatal error: gtk/gtk.h: No such file or directory
 #include <gtk/gtk.h>
          ^~~~~~~~~~~
compilation terminated.
../../../Makefile-commands:131: recipe for target 'backendxlib.o' failed
make[3]: *** [backendxlib.o] Error 1
make[3]: Leaving directory '/home/local/smooth/classes/backends/xlib'
../../Makefile-commands:107: recipe for target 'allcmds' failed
make[2]: *** [allcmds] Error 2
make[2]: Leaving directory '/home/local/smooth/classes/backends'
Makefile:15: recipe for target 'backends' failed
make[1]: *** [backends] Error 2
make[1]: Leaving directory '/home/local/smooth/classes'
Makefile:279: recipe for target 'objects' failed
make: *** [objects] Error 2
```

So I tried to install the GTK and the installer reported unmet dependencies on and on .... 

Apparently I need several libraries before I can compile the fre:ac code, but so far no success.

If anyone has compiled and installed fre:ac and/or can help me here many thanks ahead of time.
My goal in doing this is to learn the compile and install. I'm sure I can install some snap which has fre:ac ready to go, but I want to start working with C++ programming and take full advantage of my Ubuntu environment.

---

### Post by CatKiller on 2021-01-30
Generally most project pages will say what the prerequisites are for compiling their code.

Header files are generally in separate packages to the binary files, since they aren't needed for just using whatever library or application it is. On Ubuntu those packages are usually called <*package name*>-dev.

If a package is in the repositories already, and you're just compiling your own (newer/patched/whatever) version, there's a command (which I can't remember off the top of my head, since it's not something I do) to automatically pull in all the build dependencies for that package. I have no idea if the thing you're wanting to compile is one of those.

---

### Post by michael351 on 2021-01-30
I need GTK apparently - but have not been able to find it where it loads the dependencies I need.

---

### Post by wmcl on 2021-01-31
You'll run into this problem more often when compiling software. The easiest way to find which package you need to install in order to get a missing file is using *apt-file*, which needs to be installed first. After initially running *sudo apt-file update* to build the package index, you can search for packages containing a file using the *apt-file search* command. I recommend using the *-x* option to specify the search string as a regular expression, because the default substring match can yield a lot of useless results to go through in order to find the right package. For your example of searching for packages containing the file *gtk.h* the command would be ```
apt-file search -x /gtk.h$
```
which gives you the result ```

libgtk-3-dev: /usr/include/gtk-3.0/gtk/gtk.h
libgtk2.0-dev: /usr/include/gtk-2.0/gtk/gtk.h
r-cran-rgtk2: /usr/lib/R/site-library/RGtk2/include/RGtk2/gtk.h

```
Depending on whether you want to compile for GTK 2 or GTK 3, libgtk2.0-dev or libgtk-3-dev is the right package. Most likely you'll be looking for the GTK 3 one.

---

