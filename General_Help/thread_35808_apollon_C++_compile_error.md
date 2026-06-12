---
title: "apollon C++ compile error"
date: 2005-05-20
forum: General Help
---

### Post by TRINIDADUBUNTU on 2005-05-20
Help, I get the following after running ./configure for apollon install file...
...
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similiar to libstd++-dev.

I've installed everything from synaptic in relation to the libstd++-dev reference on the error.  

Please help me get this thing working!!!

---

### Post by Zelut on 2005-05-20
Have you installed the compilers?  sudo apt-get install build-essential ?

I dont know why these compilers aren't installed by default but if you ever want to ./configure (compile) ANYTHING you need those build-essential packages.  Note: you will need the install CD for that as the apt-get refers to the CD for those packages.

---

### Post by TRINIDADUBUNTU on 2005-05-20
thank you very much...
packages installed and along with a couple of other's I identified on my own with Ubuntu's great package manager, I know have Apollon up and running.  Thank you fo r the help.

---

