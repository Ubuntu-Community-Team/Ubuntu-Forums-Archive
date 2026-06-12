---
title: "Compiling source in ubuntu"
date: 2007-03-21
forum: General Help
---

### Post by SunnyRabbiera on 2007-03-21
Alright I am interested in compiling source packages in ubuntu, but I am unsure on what exactly what I need to compile from source in ubuntu.
The only reason I ask is that there are some packages I am interested in that are source only and I need to know what exactly I need to have to compile source code in ubuntu.

---

### Post by alamba on 2007-03-21
sudo apt-get install build-essential

---

### Post by zvacet on 2007-03-21
Now you have build-essential.This is just example:
You downloaded some program.tar.gz
1.tar xvfz  program.tar.gz
2.cd /program
3. ./configure
4. make
5. sudo make install

---

### Post by yigal.weinstein on 2007-03-21
You should use checkinstall as it will make deb package that you can remove via synaptic, apt-get, aptitutde, dpkg etc. all of the Debian package architecture pachaging programs.  so with checkinstall,

./configure
make
sudo checkinstall

Its a good idea to use checkinstall for source packages.  Some people don't like the program because if you aren't careful with ./configure it can complain unecessarily but it is far superior to just make install.

How sad the guy who posted this didn't even care.

---

