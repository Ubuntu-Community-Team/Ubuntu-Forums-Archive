---
title: "Need help installing Baghira"
date: 2007-07-23
forum: General Help
---

### Post by mastercoderx on 2007-07-23
Hi everyone

I'm using Ubuntu 7.04.

I'm trying to install [Baghira]("http://en.wikipedia.org/wiki/Baghira"), using [this guide]("http://baghira.sourceforge.net/OS_Clone-en.php").


I think I did everything right from the beginning to "Compile the sources and install Baghira".

When I get to "Compile the sources and install Baghira", I cd to the baghira directory, and I enter the command ```
make -f Makefile.cvs
``` in the terminal.

However, instead of giving proper output, it gives this output: ```
:~/baghira$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2

``` 


However, as you can see from the attached screenshot, I have both autoconf and autoconf2.13 installed, and autoconf is version 2.61-3.


Please tell me what I am doing wrong and how I can install Baghira.

I'll be very thankful for any help you can give me.

---

