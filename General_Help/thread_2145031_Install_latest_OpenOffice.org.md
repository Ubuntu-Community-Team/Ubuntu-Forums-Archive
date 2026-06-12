---
title: "Install latest OpenOffice.org?"
date: 2013-05-14
forum: General Help
---

### Post by Samuel H on 2013-05-14
Hi everyone,

I would like to install the latest OpenOffice.org on Ubuntu.  I installed it using the apt PPA and it installed perfectly, but it is now saying there is a newer version available.  How do I install this?  I did experiment with downloading it, extracting the tar.gz file and installing the debs, but when I did this, Ubuntu didn't seem to be aware that it was even installed!  I couldn't associate with file types, nor could I find it in the dash.  The only way I could run it was to go to the program folder and run soffice.bin.

---

### Post by Bucky Ball on 2013-05-14
What's saying there's a newer version available? OOffice or Update Manager? If you installed through a PPA the PPA may be updated and you should just be able to do a regular update through Update Manager or a terminal.

---

### Post by Samuel H on 2013-05-14
BuckyBall - OOffice did a "Check for updates" and said that version 3.4.1 (I think it was) was available to download, but that I'd have to do it from the website.

---

### Post by Irihapeti on 2013-05-14
> **Samuel H said:**
> ...Ubuntu didn't seem to be aware that it was even installed!  I couldn't associate with file types, nor could I find it in the dash.  The only way I could run it was to go to the program folder and run soffice.bin.

I use OpenOffice 3.4.1 on several installations and don't have those problems.

This is just a guess - could you have forgotten to install the debian menus deb package? It's in a separate folder on its own (desktop-integration).

---

### Post by Samuel H on 2013-05-14
> **Irihapeti said:**
> I use OpenOffice 3.4.1 on several installations and don't have those problems.

This is just a guess - could you have forgotten to install the debian menus deb package? It's in a separate folder on its own (desktop-integration).

Nope, definitely installed the desktop-integration stuff!

---

### Post by Irihapeti on 2013-05-14
Did you remove the previous version before you installed 3.4.1?

---

### Post by Samuel H on 2013-05-14
> **Irihapeti said:**
> Did you remove the previous version before you installed 3.4.1?

I didn't have a previous version installed.  Just the default LibreOffice that came with Ubuntu 12.04, which I removed.

---

### Post by Samuel H on 2013-05-14
And I haven't installed 3.4.1!  The program told me I should install it because it is available.  I have version 3.4 which I got through the PPA package.

---

### Post by Irihapeti on 2013-05-14
I thought you mentioned a PPA, but I may have misunderstood.

Not sure what's going on, unfortunately. We may have to wait for someone else to throw light on this.

---

### Post by Samuel H on 2013-05-14
I did mention a PPA.  I ended up using the PPA because as I previously mentioned I followed the instructions to extract from the .tar.gz file but they didn't work.  Did I miss something out?

---

### Post by Irihapeti on 2013-05-14
Again, I'm guessing, but maybe you've ended up with parts from two installations.

Try this:

In a terminal, run these commands
```

dpkg -l | grep office
dpkg -l | grep ooobasis
dpkg -l | grep libre
```
(That's a lower case l, not a one.)

These will give an idea as to what's installed.

The last command should show nothing related to libreoffice (though it might show some other packages that have nothing to do with it).

The other two will show you which OpenOffice packages are installed.

---

### Post by zemega on 2013-05-14
I installed 3.4.1 through this PPA. [http://www.upubuntu.com/2013/01/install-apache-openoffice-341-from-ppa.html](http://www.upubuntu.com/2013/01/install-apache-openoffice-341-from-ppa.html) .It even gives instructions on how to do it. Remove Libreoffice and install in OpenOffice. And then I installed WPS Office. It intergrates into Ubuntu menu as well. Although not stated there,  you should completely remove precious OpenOffice and LibrOffice beforehand.

---

### Post by Samuel H on 2013-05-14
Ok, the first command (dpkg -l | grep office) gives me this:

ii  openoffice                                   3.4~precise                                      Apache OpenOffice is comprised of six
ii  openoffice.org-hyphenation                   0.6                                              Hyphenation patterns for OpenOffice.org
ii  openoffice.org-ure                           3.4.1-1                                          UNO Runtime Environment
ii  openoffice.org3                              3.4.1-1                                          Brand module for OpenOffice.org 3.4.1
ii  openoffice.org3-base                         3.4.1-1                                          Base brand module for OpenOffice.org 3.4.1
ii  openoffice.org3-calc                         3.4.1-1                                          Calc brand module for OpenOffice.org 3.4.1
ii  openoffice.org3-draw                         3.4.1-1                                          Draw brand module for OpenOffice.org 3.4.1
ii  openoffice.org3-en-gb                        3.4.1-1                                          Brand language module for OpenOffice.org 3.4.1
ii  openoffice.org3-impress                      3.4.1-1                                          Impress brand module for OpenOffice.org 3.4.1
ii  openoffice.org3-math                         3.4.1-1                                          Math brand module for OpenOffice.org 3.4.1
ii  openoffice.org3-writer                       3.4.1-1                                          Writer brand module for OpenOffice.org 3.4.1

Second command gives me this:

ii  ooobasis3.4-base                             3.4.1-1                                          Base module for OpenOffice.org 3.4
ii  ooobasis3.4-binfilter                        3.4.1-1                                          Legacy filters (e.g. StarOffice 5.2) for OpenOffice.org 3.4
ii  ooobasis3.4-calc                             3.4.1-1                                          Calc module for OpenOffice.org 3.4
ii  ooobasis3.4-core01                           3.4.1-1                                          Core module for OpenOffice.org 3.4
ii  ooobasis3.4-core02                           3.4.1-1                                          Office core module for OpenOffice.org 3.4
ii  ooobasis3.4-core03                           3.4.1-1                                          Office core module for OpenOffice.org 3.4
ii  ooobasis3.4-core04                           3.4.1-1                                          Office core module for OpenOffice.org 3.4
ii  ooobasis3.4-core05                           3.4.1-1                                          Office core module for OpenOffice.org 3.4
ii  ooobasis3.4-core06                           3.4.1-1                                          Office core module for OpenOffice.org 3.4
ii  ooobasis3.4-core07                           3.4.1-1                                          Office core module for OpenOffice.org 3.4
ii  ooobasis3.4-draw                             3.4.1-1                                          Draw module for OpenOffice.org 3.4
ii  ooobasis3.4-en-gb                            3.4.1-1                                          Language module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-base                       3.4.1-1                                          Base language module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-binfilter                  3.4.1-1                                          Legacy filters (e.g. StarOffice 5.2) for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-calc                       3.4.1-1                                          Calc language module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-draw                       3.4.1-1                                          Draw language module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-help                       3.4.1-1                                          Language help module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-impress                    3.4.1-1                                          Impress language module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-math                       3.4.1-1                                          Math language module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-res                        3.4.1-1                                          Language resource module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-en-gb-writer                     3.4.1-1                                          Writer language module for OpenOffice.org 3.4, language en_GB
ii  ooobasis3.4-gnome-integration                3.4.1-1                                          Gnome integration module for OpenOffice.org 3.4
ii  ooobasis3.4-graphicfilter                    3.4.1-1                                          Graphic filter module for OpenOffice.org 3.4
ii  ooobasis3.4-images                           3.4.1-1                                          Images module for OpenOffice.org 3.4
ii  ooobasis3.4-impress                          3.4.1-1                                          Impress module for OpenOffice.org 3.4
ii  ooobasis3.4-javafilter                       3.4.1-1                                          Java filter module for OpenOffice.org 3.4
ii  ooobasis3.4-math                             3.4.1-1                                          Math module for OpenOffice.org 3.4
ii  ooobasis3.4-ogltrans                         3.4.1-1                                          OpenGL slide transitions module for OpenOffice.org 3.4
ii  ooobasis3.4-onlineupdate                     3.4.1-1                                          Online update modul for OpenOffice.org 3.4
ii  ooobasis3.4-ooofonts                         3.4.1-1                                          Mailcap module for OpenOffice.org 3.4
ii  ooobasis3.4-ooolinguistic                    3.4.1-1                                          Linguistic module for OpenOffice.org 3.4
ii  ooobasis3.4-pyuno                            3.4.1-1                                          Pyuno module for OpenOffice.org 3.4
ii  ooobasis3.4-testtool                         3.4.1-1                                          Testtool module for OpenOffice.org 3.4
ii  ooobasis3.4-writer                           3.4.1-1                                          Writer module for OpenOffice.org 3.4
ii  ooobasis3.4-xsltfilter                       3.4.1-1                                          XSLT filter samples module for OpenOffice.org 3.4


Third command gives me:

ii  djvulibre-bin                                3.5.24-9                                         Utilities for the DjVu image format
ii  libdjvulibre-text                            3.5.24-9                                         Linguistic support files for libdjvulibre
ii  libdjvulibre21                               3.5.24-9                                         Runtime support for the DjVu image format
ii  libreadline6                                 6.2-8                                            GNU readline and history libraries, run-time libraries
ii  libreadonly-perl                             1.03-3                                           facility for creating read-only scalars, arrays and hashes
ii  librest-0.7-0                                0.7.12-1ubuntu2                                  REST service access library

---

### Post by Samuel H on 2013-05-14
Ok, it's working!

I used apt-get --purge OpenOfficeorg to remove the software, then I downloaded the package and used the dpkg -i command to install all the debs.  Then I installed the desktop-integration debs, and it is all working now!

In short I have no idea what I did wrong last time, but it is working!  Thanks everyone for your help!

---

### Post by Irihapeti on 2013-05-14
Possibly there was something still hidden somewhere in a cache, and the --purge command removed it. (That was going to be my next suggestion, out of desperation more than anything. :) )

Good to know that it's working.

---

