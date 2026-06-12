---
title: "Keytouch 2.4 question...."
date: 2008-02-11
forum: General Help
---

### Post by James- on 2008-02-11
I downloaded the new beta 2.4 from [http://keytouch.sf.net](http://keytouch.sf.net) of Keytouch(we must compile)

> 
The compiling and installation procedure differs a bit from the common procedure.
Read the following steps:
1. Go to the unpacked directory.
2. Run: ./configure
3. Run to compile: make
4. Run (as root) to install: make install
5. Go to the directory keytouch-config by running: cd keytouch-config
   ... and repeat steps 2-4.
6. Go to the directory keytouch-keyboard in the unpacked directory by running: cd ../keytouch-keyboard
   ... and repeat steps 2-4.

NOTE: If you are using Ubuntu (or another sudo using distribution) open keytouch-keyboard/keytouch-keyboard in your favorite text-editor and replace "gksu" by "gksudo".


which I did and compiled it ok... I was wondering on how I go about installing it/running it....

---

### Post by zvacet on 2008-02-12
If you compiled it that means you install it.Look for icon somewhere or try to run it from terminal by typing keytouch.

---

### Post by Guinness70 on 2008-04-11
carefull with keyTouch ... 8/10 it will mess up your CTRL key (and maybe ALT and some more)
i installed it from Sourceforge and now im searching for a way to get rid of whatever it did.
do a Search here and you'll find some threads with problems as a result from keyTouch.
wish i had searched first! but from now on ill do a search before trying any "miracle oil".

my short Ubuntu life story so far:  try fix something = mess up something else...

---

