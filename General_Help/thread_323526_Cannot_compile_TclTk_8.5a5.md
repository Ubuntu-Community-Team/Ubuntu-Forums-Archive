---
title: "Cannot compile Tcl/Tk 8.5a5"
date: 2006-12-22
forum: General Help
---

### Post by Fibonacci on 2006-12-22
Hello,

I'm trying to compile Tcl and Tk 8.5a5 under Edgy (which I need for, amongst other things, aMSN with antialiased fonts) with the sources downloaded right from [http://www.tcl.tk](http://www.tcl.tk) which have worked under other distros. Tcl works fine, but Tk has some problems: ./configure --prefix=/usr/local --enable-shared --enable-xft prints a warning that it "Can't find xft configuration", and typing make produces this error messages:
```
gcc -pipe -O2    -Wl,--export-dynamic  tkAppInit.o -L/home/fibonacci/sources/tk8.5a5/unix -ltk8.5 \
                -L/home/fibonacci/sources/tcl8.5a5/unix -ltcl8.5  -lX11  -ldl  -lieee -lm  -Wl,-rpath,/usr/local/lib -o wish
/home/fibonacci/sources/tk8.5a5/unix/libtk8.5.so: undefined reference to `XScreenSaverAllocInfo'
/home/fibonacci/sources/tk8.5a5/unix/libtk8.5.so: undefined reference to `XScreenSaverQueryInfo'
/home/fibonacci/sources/tk8.5a5/unix/libtk8.5.so: undefined reference to `XScreenSaverQueryExtension'
/home/fibonacci/sources/tk8.5a5/unix/libtk8.5.so: undefined reference to `XScreenSaverQueryVersion'
collect2: ld returned 1 exit status
make: *** [wish] Error 1
```

It's probably some dev package I'm missing - but I don't know which one.

Now, I remember having seen not long ago a thread discussing how to get antialiased fonts on aMSN without compiling. I do not want that. I want my Tcl/Tk installation to be compiled with my flags (no Gentoo jokes, please :P); besides, I'm using SVN for aMSN, and might switch to nightly releases of Tcl/Tk in the future, so installing some .deb packages is obviously out of the question for me.

Could you please help me with this package?

Thanks in advance,

-Fibo

---

### Post by Fibonacci on 2006-12-22
Nevermind, I solved it just by means of deleting and re-extracting the sources from the downloaded tarball.

---

