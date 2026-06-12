---
title: "Install Adobe Reader"
date: 2020-07-20
forum: General Help
---

### Post by suomalainen on 2020-07-20
Although Adobe no longer supports Adobe reader for Linux I would like to install the last version (9.5 or something)

Does anyone know where I can find the file to do this?

Thanks!

---

### Post by TheFu on 2020-07-20
Will none of the F/LOSS options or commercial native PDF solutions work?

If you must have an old version, the best solution is probably to build a virtual machine running the last supported Linux for that software and install it there - assuming you can find it.  That's the easiest way to avoid all the library dependency problems that are certain to happen.

---

### Post by Holger_Gehrke on 2020-07-20
First hit on duckduckgo is 'https://linuxconfig.org/how-to-install-adobe-acrobat-reader-on-ubuntu-18-04-bionic-beaver-linux' which gives the address for the package as 
[ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.deb](ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.deb) and also tells you what you need in terms of dependencies. There's also a snap that packages wine and a more modern version of Acrobat Reader, and that's probably the better option, even though snaps are generally not my thing.

Holger

---

### Post by suomalainen on 2020-07-20
what is a snap?

---

### Post by monkeybrain20122 on 2020-07-20
Why do you want it? If you tell people your actual need there may be better solutions. Adobe is bloated and outdated and for the most part not even needed.

---

