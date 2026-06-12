---
title: "Reverse &quot;make install&quot;"
date: 2007-07-10
forum: General Help
---

### Post by B-Con on 2007-07-10
When I download and compile a program from source, is there a way to remove it after I've installed it?

Ex, if I do the traditional "make" then "make install", is there any sort of "make remove" that would undo what "make install" does? I kind of hate having litter around my system from programs I installed in the past but no longer want/need.

---

### Post by jazzgossen on 2007-07-10
If you use checkinstall, there is. Otherwise, there is no easy way, other than tracking down what "make install" did, and undoing it manually. Install checkinstall, and then do "checkinstall make install". That will make a package out of your newly compiled program, that you can remove with apt-get or whatever.

---

### Post by jaytek13 on 2007-07-10
Additionally, you will sometimes have the option of going into the directory of the program you compiled and do a "make uninstall." Unfortunately this isn't a standard and will not necessarily work for every program, but it's worth trying out before installing special software.

---

### Post by Nekiruhs on 2007-07-10
You can. Re-download the source for whatever. cd into the folder and then ./configure --prefix=/usr then make uninstall. It reads the makefile and undoes it.

---

### Post by B-Con on 2007-07-10
Thanks, guys.

---

