---
title: "Can't install program"
date: 2007-04-18
forum: General Help
---

### Post by Ne0z on 2007-04-18
i've been trying to install this program called

Robocup Refbox 

its available at [http://sourceforge.net/projects/msl-refbox]("http://sourceforge.net/projects/msl-refbox")

when i first trying to complile is it says im missing the QT libraries , so i tried installing anything related to QT. Tried several times but it still doesn't work stating the QT i installed isn't right.

can any kind soul try installing it and teach me how to do so . im suppose to get the GUI as seen from the screenshots at the site above. i'm still quite new at linux , so would really appreciate if you guys lend me a hand. 

thank you ! cheers

---

### Post by Perfect Storm on 2007-04-18
Can you please post the output of what is happening?

Also in most cases you need either the headers or -dev of a libs when compiling.

---

### Post by Ne0z on 2007-04-18
i got this error. 

> make -C src bin
make[1]: Entering directory `/home/name/msl-refbox/src'
CardDialog.qt.cpp:162:2: error: #error "This file was generated using the moc from 3.3.6. It"
CardDialog.qt.cpp:163:2: error: #error "cannot be used with the include files from this version of Qt."
CardDialog.qt.cpp:164:2: error: #error "(The moc has changed too much.)"
make[1]: *** [CardDialog.qt.d] Error 1
make[1]: Leaving directory `/home/name/msl-refbox/src'
make: *** [bin] Error 2


i think i've installed "qt3-dev-tools_3.3.6-3ubuntu3_i386.deb" correctly. is there a way to check ?

---

### Post by Perfect Storm on 2007-04-19
Does the source uses configure script? (./configure), how's the output of it?

---

### Post by Ne0z on 2007-04-19
hi 

i've got it to run on fedora core 5 before using the library qt-devel-3.3.7-0.fc5.i386.rpm.

then to run the program is just to enter "make" and it compiles all the necessary files. 

the error output of make (in ubuntu) is as shown above in my earlier post. 

now im migrating to ubuntu and im trying to get it to work on it. 

is there a similar library like the above ?

---

### Post by Perfect Storm on 2007-04-19
Most be libqt3-headers

---

