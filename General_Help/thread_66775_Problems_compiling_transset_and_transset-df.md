---
title: "Problems compiling transset and transset-df"
date: 2005-09-18
forum: General Help
---

### Post by shawnz on 2005-09-18
I'm trying to compile my own copy of transset-df since I can't find it in apt. The binary of transset that is in apt works fine, but transset and transset-df both refuse to compile. I'm currently using breezy now, but I was having the exact same problem while on hoary so I'm not sure it matters...

(Note that I have libxcomposite, libxfixes, libxdamage, and libxrender installed.)

shawnz@ubuntu-server:/tmp/transset-df-4$ cat Makefile
PACKAGES=xcomposite xfixes xdamage xrender
LIBS=`pkg-config --libs ${PACKAGES}` -lm
INCS=`pkg-config --cflags ${PACKAGES}`
CFLAGS = -Wall

.c.o:
        $(CC) $(CFLAGS) $(INCS) -c $*.c

OBJS=transSet.o dsimple.o

transset-df: $(OBJS)
        $(CC) $(CFLAGS) -o $@ $(OBJS) $(LIBS)

$(OBJS): dsimple.h

install:
        cp transset-df /usr/bin

clean:
        rm -f $(OBJS) transset-df
shawnz@ubuntu-server:/tmp/transset-df-4$ make
cc -Wall `pkg-config --cflags xcomposite xfixes xdamage xrender` -c transSet.c
Package xcomposite was not found in the pkg-config search path.
Perhaps you should add the directory containing `xcomposite.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xcomposite' found
transSet.c:15:22: error: X11/Xlib.h: No such file or directory
transSet.c:16:23: error: X11/Xatom.h: No such file or directory
In file included from transSet.c:17:
dsimple.h:46: error: syntax error before ‘*’ token
dsimple.h:46: warning: type defaults to ‘int’ in declaration of ‘dpy’
dsimple.h:46: warning: data definition has no type or storage class
dsimple.h:70: error: syntax error before ‘*’ token
dsimple.h:70: warning: type defaults to ‘int’ in declaration of ‘Open_Display’
dsimple.h:70: warning: data definition has no type or storage class
dsimple.h:72: error: syntax error before ‘*’ token
dsimple.h:72: warning: type defaults to ‘int’ in declaration of ‘Open_Font’
dsimple.h:72: warning: data definition has no type or storage class
dsimple.h:74: error: syntax error before ‘ReadBitmapFile’
dsimple.h:74: warning: type defaults to ‘int’ in declaration of ‘ReadBitmapFile’dsimple.h:74: warning: data definition has no type or storage class
dsimple.h:76: error: syntax error before ‘Select_Window_Args’
dsimple.h:76: warning: type defaults to ‘int’ in declaration of ‘Select_Window_Args’
dsimple.h:76: warning: data definition has no type or storage class
dsimple.h:102: error: syntax error before ‘Bitmap_To_Pixmap’
dsimple.h:102: warning: type defaults to ‘int’ in declaration of ‘Bitmap_To_Pixmap’
dsimple.h:102: warning: data definition has no type or storage class
dsimple.h:103: error: syntax error before ‘Select_Window’
dsimple.h:103: warning: type defaults to ‘int’ in declaration of ‘Select_Window’dsimple.h:103: warning: data definition has no type or storage class
dsimple.h:104: error: syntax error before ‘Get_Window_Under_Cursor’
dsimple.h:104: warning: type defaults to ‘int’ in declaration of ‘Get_Window_Under_Cursor’
dsimple.h:104: warning: data definition has no type or storage class
dsimple.h:106: error: syntax error before ‘Window_With_Name’
dsimple.h:106: warning: type defaults to ‘int’ in declaration of ‘Window_With_Name’
dsimple.h:106: warning: data definition has no type or storage class
dsimple.h:107: error: syntax error before ‘Window_With_Name_Regex’
dsimple.h:107: warning: type defaults to ‘int’ in declaration of ‘Window_With_Name_Regex’
dsimple.h:107: warning: data definition has no type or storage class
dsimple.h:108: error: syntax error before ‘Window_With_Name_Regex_Recurse’
dsimple.h:108: warning: type defaults to ‘int’ in declaration of ‘Window_With_Name_Regex_Recurse’
dsimple.h:108: warning: data definition has no type or storage class
transSet.c:24: error: syntax error before ‘target_win’
transSet.c:24: warning: type defaults to ‘int’ in declaration of ‘target_win’
transSet.c:24: warning: data definition has no type or storage class
transSet.c:67: error: syntax error before ‘get_top_window’
transSet.c:67: error: syntax error before ‘*’ token
transSet.c:67: warning: return type defaults to ‘int’
transSet.c: In function ‘get_top_window’:
transSet.c:68: error: ‘Window’ undeclared (first use in this function)
transSet.c:68: error: (Each undeclared identifier is reported only once
transSet.c:68: error: for each function it appears in.)
transSet.c:68: error: syntax error before ‘parent’
transSet.c:70: error: ‘child_list’ undeclared (first use in this function)
transSet.c:73: warning: implicit declaration of function ‘XQueryTree’
transSet.c:73: error: ‘child’ undeclared (first use in this function)
transSet.c:73: error: ‘root’ undeclared (first use in this function)
transSet.c:73: error: ‘parent’ undeclared (first use in this function)
transSet.c:86: warning: control reaches end of non-void function
transSet.c: In function ‘main’:
transSet.c:195: warning: format ‘%lx’ expects type ‘long unsigned int *’, but argument 3 has type ‘int *’
transSet.c:197: warning: format ‘%ld’ expects type ‘long int *’, but argument 3 has type ‘int *’
transSet.c:211: warning: implicit declaration of function ‘RootWindow’
transSet.c:220: warning: implicit declaration of function ‘XFetchName’
transSet.c:233: error: ‘Atom’ undeclared (first use in this function)
transSet.c:233: error: syntax error before ‘actual’
transSet.c:240: warning: implicit declaration of function ‘XGetWindowProperty’
transSet.c:240: warning: implicit declaration of function ‘XInternAtom’
transSet.c:240: error: ‘False’ undeclared (first use in this function)
transSet.c:241: error: ‘XA_CARDINAL’ undeclared (first use in this function)
transSet.c:241: error: ‘actual’ undeclared (first use in this function)
transSet.c:244: error: ‘None’ undeclared (first use in this function)
transSet.c:247: warning: implicit declaration of function ‘XFree’
transSet.c:275: warning: implicit declaration of function ‘XDeleteProperty’
transSet.c:278: warning: implicit declaration of function ‘XChangeProperty’
transSet.c:279: error: ‘PropModeReplace’ undeclared (first use in this function)transSet.c:281: warning: implicit declaration of function ‘XSync’
make: *** [transSet.o] Error 1
shawnz@ubuntu-server:/tmp/transset-df-4$

---

### Post by shawnz on 2005-09-18
Silly me, I had libxcomposite installed, but not libxcomposite-dev.

Anyway, the checkinstalled deb file if anyone wants it.

---

### Post by iggykoopa on 2006-06-26
thanks alot for the package..i had trouble compiling as well and it works great now

---

