---
title: "Can't install octave3.8 due to missing shared object error with libfltk"
date: 2014-07-18
forum: General Help
---

### Post by beakdan2 on 2014-07-18
Hi all-

I'm trying to install Octave (sudo apt-get install octave) but getting an error:
octave: error while loading shared libraries: libfltk_gl.so.1.1: cannot open shared object file: No such file or directory

I nominally have fltk1.3 installed- I have libfltk1.3, libfltk1.3-dev, libmgl-fltk7.0.0 are all showing as installed within synaptic.  However, "locate libfltk" produces no results.  (this was unchanged when I downgraded to libfltk1.1)

Where should libfltk and the associate shared objects be showing up?

---

### Post by silex89 on 2014-07-18
Hi there! :)

Maybe a shot in the dark...But have you tried to issue a sudo apt-get -f install ?

Best of luck :D

---

### Post by beakdan2 on 2014-07-18
I did try the -f flag, but thanks.

I should mention that strictly speaking, I'm running Mint 17, which is built on Trusty.  This issue seems much deeper than superficial desktop preference, though.

---

### Post by beakdan2 on 2014-07-18
SOLVED:
I installed fltk directly from source.  Got the tarball from [http://www.fltk.org/software.php](http://www.fltk.org/software.php)

did the standard configure/make/install routine, and it installed to /usr/local/include/FL

---

