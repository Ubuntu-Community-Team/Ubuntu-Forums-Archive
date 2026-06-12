---
title: "gdk_cairo_create undefined reference"
date: 2014-08-14
forum: General Help
---

### Post by timhirrel on 2014-08-14
I just upgraded toubuntu 14.04 which also upgraded me to codeblocks 13.12. I have somelongstanding programs, built and run with manygenerations of ubuntu and codeblocks. The debug versions of these programs build and run with the latest generations but the releaseversions won't build with the error:


undefined referenceto symbol 'gdk_cairo_create' 


file:
/usr/lib/x86_64-linux-gnu/libwx_gtk2u_core-2.8.so


I will appreciatehelp resolving this.

---

### Post by timhirrel on 2014-09-10
i've continued to work on this without resolution (fortunately i still have the ability to build with the earlier versions). the calls to cairo are all contained in one project. if that project is built as a dynamic library, all is good, but if the project is built as a static library the above error occurs. the build options for the project include the following:
compiler options:
`pkg-config gtk+-2.0 --cflags`
`wx-config --cflags`
`pkg-config --cflags --libs cairo`
-fPIC
linker options:
`pkg-config --libs gtk+-2.0`

again, any help will be appreciated.

---

### Post by fabien5 on 2014-11-19
Hello Tim, 
I had the same problem, 
I've found the solution here -> [URL="http://ubuntuforums.org/showthread.php?t=2113828"]http://ubuntuforums.org/showthread.php?t=2113828
[/URL]
In your Makefile, you need to put the linker option GLIBS at the end and the LFLAGS at the beginning like this:
g++ -Wall -c -g `pkg-config --cflags gtk2+-2.0 cairo` -o project main.cpp `pkg-config --libs gtk+-2.0 cairo`

it works for me !
But Im using a personal makefile, Ive seen you use codeblock, I'm totally ignorant about their compilation option..
cheers

---

