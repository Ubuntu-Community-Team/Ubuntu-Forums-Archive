---
title: "Install gtkpod-0.99.12 from tar.gz package not found when installed."
date: 2007-12-25
forum: General Help
---

### Post by jtreach on 2007-12-25
Heya I'm trying to install gtkpod-0.99.12 from a tar.gz file. When I get to the ./configure stage I get an error saying "checking for LIBGLADE... no configure: error: *** No package 'libglade-2.0' found" I checked in synaptic and I have got libglade-2.0 installed.

What am I doing wrong? I really need this as I'm trying to get my new iPod Classic working.

Thanks in advance.

---

### Post by TidusBlade on 2007-12-25
Not sure what the problem can be but maybe you can try reinstalling libglade-2.0 ?

---

### Post by obfusco on 2007-12-25
When compiling from source (.tar.gz) the libraries that you want are usually the *-dev versions.  Try installing libglade2-dev

---

### Post by kpkeerthi on 2007-12-26
To install the packages needed for compiling a source package, run
**apt-get build-dep <package>**
where <package> is the name of the package you are going to build. This will automatically download the required -dev packages from the repository.

To download the -dev dependencies for gtkpod, run **apt-get build-dep gtkpod**.

Hope it helps.

---

### Post by jtreach on 2007-12-26
Thanks I've managed to do it now, I had to install all the dependecies serperately using synaptic.

---

### Post by bfkeats on 2007-12-26
I installed libglade-dev, but I'm still having the same error. What package did you install?

*** Edit: OK, I had to install libglade2-dev. The rest of the dependencies had -dev appended where available.

---

### Post by Sikon on 2008-01-02
I've built a gtkpod-aac 0.99.12 package for Gutsy in my PPA:

[http://launchpad.net/~sikon/+archive](http://launchpad.net/~sikon/+archive)

---

