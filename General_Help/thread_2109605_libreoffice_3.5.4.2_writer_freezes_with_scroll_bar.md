---
title: "libreoffice 3.5.4.2 writer freezes with scroll bar"
date: 2013-01-28
forum: General Help
---

### Post by claracc on 2013-01-28
Hello, I have an hp compaq 6720s laptop dual boot win vista/ ubuntu 12.04 with gnome fallback desktop.

I have installed the default libreoffice of precise, i.e. 3.5.4.2

I am doing a .odt document with writer including text and images .jpg and .bmp downloaded from web, the document is about 9 pages with 12 images. When I click on scroll bar to go up and down the document, screen  freezes for about 20-25 seconds or so, till it recovers and moves to the desired part of the document. Also, I observe, when loading the document, it takes a long time to load and show the images,  unless the text is inmediatly shown but not the images.
The document is only 836 KB.

I think this is not a normal behaviour. Is there a way to avoid the freezes when moving up and down the document?. Something in settings I haven't got optimized?

Is it recommended to move to libreoffice 3.6.1 adding this ppa : [https://launchpad.net/~libreoffice/+archive/ppa/+packages](https://launchpad.net/~libreoffice/+archive/ppa/+packages) to software sources to avoid this problem?.

Thankyou very much in advance

---

### Post by omeomi on 2013-01-28
Have you tried looking at memory usage when you are using LibreOffice or scrolling? 

Also, are the images embedded or did you link to them from the web?

---

### Post by speartip on 2013-01-28
Rather than update to the 3.6 ppa, I would recommend to 1st try the 3.5 ppa from here, as 3.6 has been known to be buggy:
[https://launchpad.net/~libreoffice/+archive/libreoffice-3-5](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5)
I have also found that Apache openoffice is very stable. The deb can be downloaded from here:
[http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html)
and install instructions from here, work well:
[http://forum.openoffice.org/en/forum/viewtopic.php?t=50119](http://forum.openoffice.org/en/forum/viewtopic.php?t=50119)
I know it's not ethical for Linux users to use openoffice instead of libreoffice, but it really does feel rock solid & snappy.

---

### Post by vasa1 on 2013-01-28
> **speartip said:**
> ...
I know it's not ethical for Linux users to use openoffice instead of libreoffice, but it really does feel rock solid & snappy.

Is that necessary?

---

### Post by speartip on 2013-01-28
> **vasa1 said:**
> Is that necessary?
What do you mean by that???

Libreoffice is now the office suite of choice in nearly all Linux distros, and most Linux users prefer to use software that is community driven rather than corporation driven.
That's why I wrote what I did.
Am I wrong in making that assumption???

---

### Post by claracc on 2013-01-28
> **omeomi said:**
> Have you tried looking at memory usage when you are using LibreOffice or scrolling? 

Also, are the images embedded or did you link to them from the web?

I have checked memory settings in libreoffice an I have: see attached file.

The images are copied from web pages and pasted into document, so not linked.
I have topped memory and CPU use of sbinoffice when scrolling and there is not problem, used less than 10% memory or CPU.

About apache openoffice, I use it in my vista partition and I know it works very well. If I cannot solve the problem with libreoffice I will install it by the instructions addressed. 

I don't think is unethical to use apache OO instead of libreoffice if it works better in my system, since it is an open source software too. 

Thankyou all for responses. Any other ideas?

Also I have noticed, sometimes saving this document it takes long time too, above 30-35 seconds.

---

