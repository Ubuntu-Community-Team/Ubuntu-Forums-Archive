---
title: "Problem installing tclspice"
date: 2005-08-02
forum: General Help
---

### Post by hal8000 on 2005-08-02
Trying to install tclspice from source:
[http://tclspice.sourceforge.net/](http://tclspice.sourceforge.net/)


Have unpacked source file and also installed  packages tclreadline and BLT, but
configure fails because it cannot find a particular tcl script


anc@zen:~/tclspice$ ./configure --with-tcl --enable-experimental --enable-xspiceloading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking host system type... i686-pc-linux-gnu
checking for tclConfig.sh...
can't find Tcl configuration script "tclConfig.sh"
anc@zen:~/tclspice$


What package contains tclConfig.sh?  Using 5.04 Hoary, thanks in advance.

---

### Post by Xian on 2005-08-02
You're going to need to install a tcl-devel package.
I don't know which version you will require.

You might try tcl8.4-dev and go from there.

---

### Post by ILoveBobbyMarley on 2007-08-02
Hello, 

I had the same problem so thought I would post my solution, hope it works for you (I'm a fiesty user).

After installing the tcl8.4-dev files I had to change the ./configure arguments to 

./configure --with-tcl-version=8.4

and that seemed to do the trick.

Note, I also had to install the libxmu-dev and libxaw-dev libraries using synaptic to get the configure command to finish.

My full configure line is:

./configure --with-tcl-version=8.4 --enable-experimental --enable-xspice --prefix=/usr/share/gEDA/

Still haven't managed to get the make to work yet though ,


(crashes out with 
...
gcc -DHAVE_CONFIG_H -I. -I../../.. -I../../../src/include -I../../../src/frontend      -g -O2 -Wall  -MT x11.o -MD -MP -MF .deps/x11.Tpo -c -o x11.o x11.c
x11.c: In function ‘X11_NewViewport’:
x11.c:422: error: invalid lvalue in assignment
x11.c: In function ‘zoomin’:
...)

but these are issues for another post I guess,

peace

---

