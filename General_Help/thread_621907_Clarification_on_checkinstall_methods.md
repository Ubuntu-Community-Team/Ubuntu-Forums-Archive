---
title: "Clarification on checkinstall methods"
date: 2007-11-24
forum: General Help
---

### Post by Photon on 2007-11-24
hey guys! I just started out compiling apps on linux. And i have a doubt. I have seen quite a few ways to compile apps using checkinstall

1.
./configure
make
sudo checkinstall 

2.
./configure
make
sudo checkinstall -D make install


What is the difference between the two approaches? I know that checkinstall -D generates a deb package. Other than that what is the difference? Any help much appreciated :)

---

### Post by espressopigeon on 2007-11-24
If the command to install is not make install, you would place it after the -D such as:

sudo checkinstall -D setup

The default is make install, so

sudo checkinstall -D make install

is redundant.

---

