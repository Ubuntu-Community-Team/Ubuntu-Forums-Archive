---
title: "dependency issue: libpng2"
date: 2008-05-14
forum: General Help
---

### Post by linmix on 2008-05-14
I'm trying to install [ldglite]("http://ldglite.sourceforge.net/") and I'm following the installation instructions at [LDraw]("http://www.ldraw.org/Article107.html")

I've added the necessary repository to /etc/apt/sources.list and updated the list, but when I try to install I get the following dependency issues:

> $ sudo apt-get install ldglite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ldglite: Depends: libpng2 (>= 1.0.12) but it is not installable
           Depends: xlibosmesa3 (> 4.1.0) but it is not installable
           Depends: xlibs (> 4.1.0) but it is not installable
E: Broken packages


I'm not sure even where to start... any help is appreciated.

---

### Post by y-lee on 2008-05-14
Ok from what I see you have added a debian repo to your ubuntu source.list 

This is not a good idea but it can be done. It is rather advanced. 

Over all one should not mix repos from other distros to ubuntu. I would remove the what ever lines you added.

> deb [http://www.sslug.dk/~grove/debian/](http://www.sslug.dk/~grove/debian/) stable main
deb-src [http://www.sslug.dk/~grove/debian/](http://www.sslug.dk/~grove/debian/) stable main

or

deb [http://www.sslug.dk/~grove/debian/](http://www.sslug.dk/~grove/debian/) unstable main

---

### Post by y-lee on 2008-05-14
> I'm trying to install ldglite and I'm following the installation instructions at LDraw

If you want or need the program you are going to have to try and compile it from the source code on the ldglite web site.

Do you know how to do that and do you want to?

---

