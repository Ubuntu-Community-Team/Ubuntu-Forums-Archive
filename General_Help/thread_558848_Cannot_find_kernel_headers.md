---
title: "Cannot find kernel headers"
date: 2007-09-24
forum: General Help
---

### Post by FRuMMaGe on 2007-09-24
I recently compiled myself a custom kernel from the 2.6.22.7 build.  Everything is fine, however.

When I try to compile some programs, i get an error saying it could not find linux-headers-2.6.22.7 etc.

However, my kernel headers are called kernel-headers-2.6.22.7.

It seems the program is looking for the wrong headers.

Help!

---

### Post by FRuMMaGe on 2007-09-24
please help

---

### Post by Adramelech on 2007-09-24
read the configuration script help and change the path to your linux headers.

./configure --help

---

### Post by FRuMMaGe on 2007-09-24
Is the the configure script in each of the programs?

I would preffer a more global solution

---

### Post by Adramelech on 2007-09-24
Copy your headers to /usr/src i guess

---

### Post by FRuMMaGe on 2007-09-24
They are already there.  My problem is that the programs are looking for the package "linux-headers-2.6.22.7" but mine are called "kernel-headers-2.6.22.7".

---

### Post by Adramelech on 2007-09-24
Do a simlink:

sudo ln -s /usr/src/kernel-headers-2.6.22.7 /usr/src/linux-headers-2.6.22.7

---

### Post by FRuMMaGe on 2007-09-24
Thanks for the suggestion, but it didnt work.

It is looking for the package, not the directory.

Where does it look for the package?  If i knew it them I could just copy the compiled deb file there

---

### Post by Adramelech on 2007-09-24
it looks in a database, you can build a package and install it using dpkg or you can force the installation of the other packages.

man dpkg

and search for the correct force option

---

