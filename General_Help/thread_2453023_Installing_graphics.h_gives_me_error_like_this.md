---
title: "Installing graphics.h gives me error like this"
date: 2020-11-01
forum: General Help
---

### Post by yow2211 on 2020-11-01
```
Makefile:934: warning: overriding recipe for target 'libgraph.pc'
Makefile:409: warning: ignoring old recipe for target 'libgraph.pc'
make  all-recursive
make[1]: Entering directory '/home/mrow/Downloads/libgraph-1.0.2'
Makefile:934: warning: overriding recipe for target 'libgraph.pc'
Makefile:409: warning: ignoring old recipe for target 'libgraph.pc'
Making all in doc
make[2]: Entering directory '/home/mrow/Downloads/libgraph-1.0.2/doc'
Making all in man
make[3]: Entering directory '/home/mrow/Downloads/libgraph-1.0.2/doc/man'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/mrow/Downloads/libgraph-1.0.2/doc/man'
make[3]: Entering directory '/home/mrow/Downloads/libgraph-1.0.2/doc'
make[3]: Nothing to be done for 'all-am'.
make[3]: Leaving directory '/home/mrow/Downloads/libgraph-1.0.2/doc'
make[2]: Leaving directory '/home/mrow/Downloads/libgraph-1.0.2/doc'
make[2]: Entering directory '/home/mrow/Downloads/libgraph-1.0.2'
Makefile:934: warning: overriding recipe for target 'libgraph.pc'
Makefile:409: warning: ignoring old recipe for target 'libgraph.pc'
/bin/bash ./libtool --mode=link gcc -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DFONTDIR=\""/usr/local/share/libgraph/Font/"\" -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -o libgraph.la -rpath /usr/local/lib -version-info 1:2:0 -export-dynamic libgraph.lo text.lo shapes.lo polygon.lo  -lm -lSDL_image -L/usr/lib/x86_64-linux-gnu -lSDL 
gcc -shared  .libs/libgraph.o .libs/text.o .libs/shapes.o .libs/polygon.o  -lm -lSDL_image -L/usr/lib/x86_64-linux-gnu -lSDL  -Wl,-soname -Wl,libgraph.so.1 -o .libs/libgraph.so.1.0.2
/usr/bin/ld: .libs/text.o:/home/mrow/Downloads/libgraph-1.0.2/grtext.h:77: multiple definition of `InternalFont'; .libs/libgraph.o:/home/mrow/Downloads/libgraph-1.0.2/grtext.h:77: first defined here
/usr/bin/ld: .libs/text.o:/home/mrow/Downloads/libgraph-1.0.2/grtext.h:87: multiple definition of `TP'; .libs/libgraph.o:/home/mrow/Downloads/libgraph-1.0.2/grtext.h:87: first defined here
/usr/bin/ld: .libs/shapes.o:/home/mrow/Downloads/libgraph-1.0.2/shapes.h:121: multiple definition of `_internal_linestyle'; .libs/libgraph.o:/home/mrow/Downloads/libgraph-1.0.2/shapes.h:121: first defined here
/usr/bin/ld: .libs/shapes.o:/home/mrow/Downloads/libgraph-1.0.2/shapes.h:115: multiple definition of `_last_arc'; .libs/libgraph.o:/home/mrow/Downloads/libgraph-1.0.2/shapes.h:115: first defined here
/usr/bin/ld: .libs/polygon.o:/home/mrow/Downloads/libgraph-1.0.2/polygon.h:42: multiple definition of `_scanlist'; .libs/libgraph.o:/home/mrow/Downloads/libgraph-1.0.2/polygon.h:42: first defined here
collect2: error: ld returned 1 exit status
make[2]: *** [Makefile:377: libgraph.la] Error 1
make[2]: Leaving directory '/home/mrow/Downloads/libgraph-1.0.2'
make[1]: *** [Makefile:552: all-recursive] Error 1
make[1]: Leaving directory '/home/mrow/Downloads/libgraph-1.0.2'
make: *** [Makefile:268: all] Error 2
```


I've tried to search for the solution, but almost majority of it doesnt give clear solution, or having different error. Can someone help me what i did wrong here
This error happenned after 

./configure
make

and then error occurs

---

### Post by yapidumoac on 2020-11-02
Could you give us a clue as to a) what you are attempting to compile and b) the name of the compiler you are using.

It would also help us if you provided a [system information report]("http://www.ubuntugeek.com/system-hardware-information-and-run-reports.html")

---

### Post by yow2211 on 2020-11-03
> **yapidumoac said:**
> Could you give us a clue as to a) what you are attempting to compile and b) the name of the compiler you are using.

It would also help us if you provided a [system information report]("http://www.ubuntugeek.com/system-hardware-information-and-run-reports.html")


Okay so what was i trying to do is installing the Graphics.h into my gcc or g++ so i can use #include<graphics.h> in my program

---

### Post by Impavidus on 2020-11-03
graphics.h is a header file. It doesn't require compilation, you just put it in a directory fit for the purpose (like /usr/local/include). If gcc doesn't find it there, use the -I option for additional include directories.

But header files belong to libraries, so I guess you're trying to compile the library. What is the library called? Where did you get it? Note that compiling something from source and manually installing it are considered a last resort in Ubuntu.

---

