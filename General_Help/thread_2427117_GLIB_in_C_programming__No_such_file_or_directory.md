---
title: "GLIB in C programming:  No such file or directory"
date: 2019-09-18
forum: General Help
---

### Post by jenniferruurs on 2019-09-18
I a have C file where the 
where when I execute it via terminal:
```
gcc test.c -o test
```

I get the error 
[I]fatal error: glib-object.h: No such file or directory

[/I]I also tried ```
gcc -O2 $(pkg-config --cflags glib-2.0) -o test test.c $(pkg-config --libs glib-2.0)
```

The headers of the C file

```
#include <stdlib.h>
#include <stdio.h>
#include <glib-object.h>
#include <json-glib/json-glib.h>
```

---

### Post by Holger_Gehrke on 2019-09-18
Do you have the developers package for glib 2.0 (libglib2.0-dev) installed ? Just having the library does **not** give you the headers, they are in the *-dev packages.
Also, 'pkg-config --libs' outputs the '-l' option for the linker-part of the gcc toolchain, it doesn't produce the '-I' option for the preprocessor which gives paths for the headers. You probably want 'pkg-config --cflags --libs glib-2.0' which does both.

Holger

---

### Post by jenniferruurs on 2019-09-18
How do I install the developers package for glib 2.0?

---

### Post by Holger_Gehrke on 2019-09-18
```
sudo apt install libglib2.0-dev
```in a terminal or with synaptic.

Holger

---

### Post by jenniferruurs on 2019-09-18
After I installed:

```
sudo apt install libglib2.0-dev
```

And I execute
```
gcc test.c -o test
```

The first error:
[I]fatal error: glib-object.h: No such file or directory
[/I]
Changes in to:
*[I]fatal error: json-glib/json-glib.h: No such file or directory*



[/I]

---

### Post by TheFu on 2019-09-18
Did you install json-glib dev package?

---

### Post by Holger_Gehrke on 2019-09-18
According to [https://packages.ubuntu.com](https://packages.ubuntu.com) json-glib.h is in the package 'libjson-glib-dev'.

Holger

---

### Post by jenniferruurs on 2019-09-19
After I installed 
```
sudo apt-get install libjson-glib-dev
```

When I try
gcc test.c -o test

The first error came back:
[I]fatal error: glib-object.h: No such file or directory

[/I]When I try```
gcc -O2 $(pkg-config --cflags glib-2.0) -o test test.c $(pkg-config --libs glib-2.0)
```

Changes in to:
*[I]fatal error: json-glib/json-glib.h: No such file or directory*[/I]

---

### Post by spjackson on 2019-09-19
> **jenniferruurs said:**
> After I installed 
```
sudo apt-get install libjson-glib-dev
```

When I try
gcc test.c -o test

The first error came back:
[I]fatal error: glib-object.h: No such file or directory

[/I]When I try```
gcc -O2 $(pkg-config --cflags glib-2.0) -o test test.c $(pkg-config --libs glib-2.0)
```

Changes in to:
*[I]fatal error: json-glib/json-glib.h: No such file or directory*[/I]
You need to tell the compiler where to find the necessary from your newly added package.
```
gcc -O2 $(pkg-config --cflags glib-2.0 json-glib-1.0) -o test test.c $(pkg-config --libs glib-2.0 json-glib-1.0)
```

---

### Post by jenniferruurs on 2019-09-19
Thank you this did worked!

Is there a way how I can added these files to gcc so that 
```
gcc test.c -o test
```
Would also work?

Or isn't that possible?

---

### Post by spjackson on 2019-09-19
I am pretty sure that there isn't a straight forward way to force gcc to pick up extra include paths and extra libraries without you specifying them on the command line. In practice, a Makefile or other similar build tool would be used.

---

### Post by TheFu on 2019-09-19
+1 on using a makefile.  That's what gmake/cmake were made to handle.  I've never used cmake, but with gmake, beware that tabs and spaces in the file mean different things. Don't let the editor change tabs into spaces or spaces into tabs when dealing with Makefiles.

---

