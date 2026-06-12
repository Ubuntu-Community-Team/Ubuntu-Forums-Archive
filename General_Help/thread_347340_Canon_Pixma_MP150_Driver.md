---
title: "Canon Pixma MP150 Driver"
date: 2007-01-27
forum: General Help
---

### Post by wersdaluv on 2007-01-27
I have been hunting high and low but still haven't found a Pixma MP150 Driver for my Edgy Eft.

Do you know of a driver that I can use?

:guitar:

---

### Post by xopher on 2007-01-27
There's turboprint, which works. (But isn't free) [http://www.turboprint.info](http://www.turboprint.info)

And there's a free driver as well, don't know if it works though:

[http://pixma.schewe.com/](http://pixma.schewe.com/)

And here is something that someone said to work:

> When I had Fedora installed I used the Canon iP1500 driver, and that one worked. Maybe you should try that as well.

[ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)

---

### Post by GvS on 2007-02-01
You can install Gutenprint from CVS (currently 5.1). It has a MP150 driver.
(make sure you have installed libcupsimage2-dev, doxygen and docbook-utils, for a succesfull compilation)

Steps:

1)
open a console:
cvs -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print login
cvs -z3 -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print co -P print 

2)
go to the directrory (cd print/)
run ./autogen.sh

3)
run make clean; make
if it complains about raster.h, you can just download it here [http://www.opensource.apple.com/darwinsource/10.4.6.x86/cups-97.1/filter/raster.h](http://www.opensource.apple.com/darwinsource/10.4.6.x86/cups-97.1/filter/raster.h) I'm not saying it is the correct version, but at least it worked for me :)

4)
run sudo make install

5)
run sudo cups-genppd.5.1

If you run into errors during 'make', just check what the error is, and look it up with a search engine...

Hope it helps... for me it worked :)

P.S. attached is the PPD file I created... it is installed in /usr/share/cups/model/gutenprint/5.1
When installing the printer, navigate to that location and select the file.
Don't know if that works, but if it does, it saves you a lot of trouble :)

---

### Post by wersdaluv on 2007-02-01
> **GvS said:**
> You can install Gutenprint from CVS (currently 5.1). It has a MP150 driver.
(make sure you have installed libcupsimage2-dev, doxygen and docbook-utils, for a succesfull compilation)

Steps:

1)
open a console:
cvs -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print login
cvs -z3 -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print co -P print 

2)
go to the directrory (cd print/)
run ./autogen.sh

3)
run make clean; make
if it complains about raster.h, you can just download it here [http://www.opensource.apple.com/darwinsource/10.4.6.x86/cups-97.1/filter/raster.h](http://www.opensource.apple.com/darwinsource/10.4.6.x86/cups-97.1/filter/raster.h) I'm not saying it is the correct version, but at least it worked for me :)

4)
run sudo make install

5)
run sudo cups-genppd.5.1

If you run into errors during 'make', just check what the error is, and look it up with a search engine...

Hope it helps... for me it worked :)

P.S. attached is the PPD file I created... it is installed in /usr/share/cups/model/gutenprint/5.1
When installing the printer, navigate to that location and select the file.
Don't know if that works, but if it does, it saves you a lot of trouble :)

Wow! Thank you very much! I'll try it when I get home! :)

---

### Post by mdurham on 2007-02-02
Take a look [here]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/"), it might help.

---

### Post by CKYman on 2007-05-01
Just wanted to let anyone know that if they are trying to install this printer on feisty, use the Canon > MULTIPASS MP150 > High Quality Image (Gutenprint CUPS) (expert) driver.  Works for me.

---

### Post by wersdaluv on 2007-05-01
> **CKYman said:**
> Just wanted to let anyone know that if they are trying to install this printer on feisty, use the Canon > MULTIPASS MP150 > High Quality Image (Gutenprint CUPS) (expert) driver.  Works for me.

Thank you very much for that tip!

---

### Post by rftelc on 2007-07-11
very useful,  this help me solve the problem install MP150 on ubuntu 7.04, I can print now.:)

---

### Post by holydog on 2007-09-09
WOW. Thx dudes. Great help. Finding that driver was a big pain the *** but thx to you i need not to find! Thx in the end.

---

### Post by drsmaw on 2007-09-23
> **CKYman said:**
> Just wanted to let anyone know that if they are trying to install this printer on feisty, use the Canon > MULTIPASS MP150 > High Quality Image (Gutenprint CUPS) (expert) driver.  Works for me.

That works! no need to look any further.  Select it and go on to the next problem.

---

### Post by cotcot on 2007-09-30
I had no succes compiling gutenprint. (for an epson printer)
I ended up with this error in make and could not find a solution till now.
> ../../src/gutenprintui2/.libs/libgutenprintui2.so: undefined reference to `stp_get_external_options'
collect2: ld returned 1 exit status

---

### Post by cotcot on 2007-09-30
PROBLEM SOLVED
I have compiled gutenprint-5.1.3 (downloded from their website) using the normal way (./configure, make clean, make, sudo make install)
Then I manually made the directory /usr/share/cups/model/gutenprint/5.1.
Then I ran the command ```
sudo cups-genppd.5.1
``` as suggested by GvS (thanks, this was the clue for me) and configured the printer with cups ([http://localhost:631/](http://localhost:631/)).
Printer works.

---

### Post by orko3001 on 2007-11-08
> cvs -d:pserver:anonymous@gimp-print.cvs.sourceforge.net:/cvsroot/gimp-print login

I get asked for my CVS Password. My su pass doesn't work. How so I set CVS password?

Cheers

---

