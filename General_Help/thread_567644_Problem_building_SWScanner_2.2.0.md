---
title: "Problem building SWScanner 2.2.0"
date: 2007-10-04
forum: General Help
---

### Post by Agent_Bain on 2007-10-04
Hello, I'm trying to compile the SWScanner 2.2.0 source from the tar on their site. When I do a ./configure I get the following error at the end.

checking for MAXPATHLEN... 4096
checking for main in -lshp... no
configure: error:       Can't find shapelib library (libqshp.so).
                        Be sure you have it installed, and try using --with-extra-libs argument
                        followed with the path where the libshp.so file is, to allow configure
                        find it out of standard locations.

I've tried sudo apt-get install shapelib, and google without any success.

Any ideas?

Thanks

---

### Post by seppoV8 on 2008-04-03
i installed also packages libshp-dev and libqt4-dev

---

### Post by calraith on 2008-05-23
For what it's worth, I built a .deb for Hardy of the SVN version of SWScanner.  [http://headcandy.org/rojo/swscanner/](http://headcandy.org/rojo/swscanner/)

---

