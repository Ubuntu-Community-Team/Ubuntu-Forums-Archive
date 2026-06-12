---
title: "installing kxmame causes autoconf error"
date: 2007-12-28
forum: General Help
---

### Post by thebluedino on 2007-12-28
I've been attempting to compile kxmame and have come across this error

> matt@matt-desktop:~/Desktop/kxmame/trunk$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 653: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
matt@matt-desktop:~/Desktop/kxmame/trunk$ 


I have autoconf 2.61-4 installed as well as the libraries required per the readme so I'm not sure how to resolve this

I'm new to this so please forgive my ignorance but any help would be appreciated

---

### Post by calvarymanagua on 2007-12-29
I had the same problem.  I did a few things and I finally got it to work.  I installed kde-devel and unistalled autoconf 2.13 (not sure if this is necessary).  I also had to install automake 1.9.  It finally worked.  

Hope this helps

---

