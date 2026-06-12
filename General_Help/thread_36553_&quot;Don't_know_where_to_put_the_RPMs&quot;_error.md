---
title: "&quot;Don't know where to put the RPMs&quot; error on install of HPI drivers..."
date: 2005-05-23
forum: General Help
---

### Post by jxn on 2005-05-23
because there is no .deb package for audioscience's drivers ([www.audioscience.com](www.audioscience.com)) for their professional hardware equipment, I've got to install it from the source...but when I run ./compile, I get a strange "Don't know where to put the RPMs" error... any idea what I could be missing out on?

---

### Post by SGC on 2005-05-23
Is this the package that you try to install:
[http://www.audioscience.com/internet/download/hpklinux-2.92.tar.gz](http://www.audioscience.com/internet/download/hpklinux-2.92.tar.gz)

If so, it seems like an ordinary source package, you can install it with:
./configure
make
make install
For more options read the file INSTALL.hpi inside the package

If this is not the package, please post the URL of the package that you try to install

---

### Post by jxn on 2005-05-23
[QUOTE=SGC]Is this the package that you try to install:
[http://www.audioscience.com/internet/download/hpklinux-2.92.tar.gz](http://www.audioscience.com/internet/download/hpklinux-2.92.tar.gz)

If so, it seems like an ordinary source package, you can install it with:
./configure
make
make install
For more options read the file INSTALL.hpi inside the package

If this is not the package, please post the URL of the package that you try to install[/QUOTE]
Yes, that's the package... And i was installing using 
```

./configure
make
make install
```
as I regularly do (on Gentoo systems, I'm new to ubuntu and binary distributions as a whole, but I need this machine for work)...I have already read the INSTALL.hpi file contents.  This error comes after a long train of successful tests during "./configure" -- I'm not at the machine now, but I doubt the prior output from "./configure" would be helpful as it was just a series of successful tests which were unrelated to RPM packages as far as I can tell.

---

### Post by nlz on 2008-07-17
I've got the exact same problem with the exact same package. What was your solution?

---

### Post by PmDematagoda on 2008-07-17
Trying to get your answer from a thread that is more than 3 years old is not really the way to solve your problems, if you must find the solution then it is better to create a thread of your own since that is usually more effective.

This thread is closed.

---

### Post by PmDematagoda on 2008-07-24
While I don't do this often(actually this is the first time), after a few PMs between nlz, I have agreed to post the following solution on his behalf. If you have any questions concerning this solution, then please ask nlz himself, all credit to this solution must go to nlz himself since this is not my answer whatsoever.

Solution(As quoted):-
> The installers that Audio Science supplies are in their scripts looking for Mandrake or Suse architecture. I've tried building around this, but everything seems to go wrong in the make file.

Audio Science also will not give support for products two year after their release.


Installing Suse did the trick for me.

---

