---
title: "gimpshop for ubuntu?"
date: 2005-09-05
forum: General Help
---

### Post by OpposingForce on 2005-09-05
Ok well I tried getting the .deb package from here for gimpshop and did the command to install debian packages

"sudo dpkg -i filegoeshere.deb"

[http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&zu=http%3A%2F%2Fmirror.suramya.com%2F](http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&zu=http%3A%2F%2Fmirror.suramya.com%2F)

unfortunatly that broke my gimp install and it wouldnt start any more...when I try to start it from the command line

"gimp %u"

I get this error:

"gimp: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by gimp)"


so I had to reinstall GIMP..which is no longer in my applications menu :( .. 

anyway what am I doing wrong...i tried this twice and I cant figure out how to install gimpshop someone please help!

---

### Post by arnieboy on 2005-09-05
[QUOTE=OpposingForce]I get this error:

"gimp: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.3.4' not found (required by gimp)"


so I had to reinstall GIMP..which is no longer in my applications menu :( .. 

anyway what am I doing wrong...i tried this twice and I cant figure out how to install gimpshop someone please help![/QUOTE]
u shd read the whole tutorial here:
[http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/)
glibc 2.3.4 is not there in hoary. its got an older version. gimpshop has several dependencies including the one mentioned.

---

### Post by FishFoot on 2005-09-17
I've done this a little differently, here's what I did.

I grabbed the source from the [here](http://plasticbugs.com/index.php?p=288) 

After decompressing it I ran ./configure and got a slew of errors.

1) XML:Parser
    solution: sudo apt-get install libxml-perl

2) Can't complie because missing GTK:
    solution sudo apt-get install libgtk2.0-dev

3) checking for libart-2.0... Package libart-2.0 was not found in the pkg-config search path.
    solution:  sudo apt-get install libart-2.0-dev

4) Checks for TIFF libary failed.
    solution:  sudo apt-get install libtiff4-dev

5) Checks for JPEG library failed.
    solution: sudo apt-get install libjpeg-dev

6) Checks for PNG library failed.
    solution: sudo apt-get install libpng-dev

7) Check for libgimpprint failed. 
    solution: sudo apt-get install libgimpprint-dev

Then it BUILT!!!  YEAH!!!


Have fun my friends
FishFoot

---

### Post by Blue1k on 2005-09-18
I tried your way but I get this:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

What library am I missing?

Thanks!

---

### Post by arnieboy on 2005-09-18
[QUOTE=Blue1k]I tried your way but I get this:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

What library am I missing?

Thanks![/QUOTE]
do a :
```
sudo apt-get install gcc
```
and all will be fine

---

### Post by Blue1k on 2005-09-20
LOL..one more error. I'm gonna see if I can track down the proper lib but if anyone can beat me to it that would be great.

configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

Apparently my cpp is insane :razz:

---

### Post by Blue1k on 2005-09-20
I figured it out-needed g++

---

### Post by thewax on 2005-10-21
[QUOTE=FishFoot]I've done this a little differently, here's what I did.

I grabbed the source from the [here](http://plasticbugs.com/index.php?p=288) 

After decompressing it I ran ./configure and got a slew of errors.

1) XML:Parser
    solution: sudo apt-get install libxml-perl

2) Can't complie because missing GTK:
    solution sudo apt-get install libgtk2.0-dev

3) checking for libart-2.0... Package libart-2.0 was not found in the pkg-config search path.
    solution:  sudo apt-get install libart-2.0-dev

4) Checks for TIFF libary failed.
    solution:  sudo apt-get install libtiff4-dev

5) Checks for JPEG library failed.
    solution: sudo apt-get install libjpeg-dev

6) Checks for PNG library failed.
    solution: sudo apt-get install libpng-dev

7) Check for libgimpprint failed. 
    solution: sudo apt-get install libgimpprint-dev

Then it BUILT!!!  YEAH!!!


Have fun my friends
FishFoot[/QUOTE]

hey :)
im trying this but i get an error when trying to install libxml-perl with synaptic (or apt-get)

 libxml-perl:
 Depends: libxml-parser-perl  but it is not installable

when i try installing libxml-parser-perl i get:
libdbix-xml-rdb-perl:
 Depends: libdbi-perl (>=1.00) but it is not installable

and libdbi-perl isn't even in the package list


how can i solve this?
greets

---

