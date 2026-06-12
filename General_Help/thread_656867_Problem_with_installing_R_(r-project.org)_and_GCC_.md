---
title: "Problem with installing R (r-project.org) and GCC compatibility"
date: 2008-01-03
forum: General Help
---

### Post by Perci on 2008-01-03
I think that I successfully installed R (the statistics/bioinformatics environment and language from [www.r-project.org](www.r-project.org) but I didn't know beforehand that xubuntu feisty didn't come with gcc.  During the R install I noticed R installing some gcc things as dependencies.  No I have some or all of gcc but there seems to be a conflict problem:

user1@user1-desktop:~$ aptitude show gcc
Package: gcc
State: installed
Automatically installed: no
Version: 4:4.1.2-1ubuntu1
Priority: optional
Section: devel
Maintainer: Ubuntu Core developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 65.5k
Depends: cpp (>= 4:4.1.2-1ubuntu1), gcc-4.1 (>= 4.1.2)
Recommends: libc6-dev | libc-dev
Suggests: make, manpages-dev, autoconf, automake1.9, libtool, flex, bison, gdb,
          gcc-doc
Conflicts: gcc-doc (< 1:2.95.3)
Provides: c-compiler
Description: The GNU C compiler
 This is the GNU C compiler, a fairly portable optimizing compiler for C. 
 
 This is a dependency package providing the default GNU C compiler.

user1@user1-desktop:~$

See where it says Conflicts?  How can I fix this?
Also, here's  the log of when I installed R:

---

### Post by Perci on 2008-01-03
...continued

I should also point out that I before installing R, no mention was made in their faqs/docs or readme that gcc was necessary for installing but maybe I should have assumed this?

This is what I added to my /etc/apt/sources.list
deb [http://cran.cnr.berkeley.edu/bin/linux/ubuntu](http://cran.cnr.berkeley.edu/bin/linux/ubuntu) feisty/

And this attachment is my log from adding the secure-apt key and doing apt-get update right before the install:  sudo apt-get install r-base (this log from this is in my previous message).

Please help me out guys and gals.

---

### Post by shirilover on 2008-01-03
The conflicts list item indicated packages and their version which are incompatible with the program you are checking. So long as the version of gcc-doc is greater than the listed conflict, you will not run into a problem.

As for needing gcc, r-base depends on libgcc1 which depends on gcc4.1-base, this is why gcc was installed.

---

### Post by Perci on 2008-01-03
Shirilover,

Oh, OK!  Thanks a lot.  I understand now.  That also explains why R didn't even have to install gcc-doc, which I could retrieve from the repositories in the future if I need it.

user1@user1-desktop:~$ dpkg -l | grep libgcc1
ii  libgcc1                                    4.1.2-0ubuntu4                         GCC support library
user1@user1-desktop:~$ dpkg -l | grep gcc-doc
user1@user1-desktop:~$ aptitude show gcc-doc
Package: gcc-doc
State: not installed
Version: 4:4.1.2-1ubuntu1
Priority: optional
Section: devel
Maintainer: Ubuntu Core developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: gcc-4.1-doc (>= 4.1.2)
Suggests: gcc (>= 4:4.1.2-1ubuntu1)
Description: Documentation for the GNU C compilers (gcc, gobjc, g++)
 Documentation for the GNU compilers in info format (dependency package).

user1@user1-desktop:~$

Thanks again,
Perci

---

