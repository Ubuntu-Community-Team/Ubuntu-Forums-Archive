---
title: "Anybody have experience connecting wii controller?"
date: 2008-01-10
forum: General Help
---

### Post by tictacman on 2008-01-10
I'm looking to use a wii controller together with a bluetooth usb adapter on ubuntu 7.10. I'm trying to follow a tutorial for a basic setup and i'm running into problems installing libwiimote

This is the tutorial i'm following: [https://help.ubuntu.com/community/CWiiD#head-0757d4dab188c92b3b419eb0c066100ce2110308](https://help.ubuntu.com/community/CWiiD#head-0757d4dab188c92b3b419eb0c066100ce2110308)

After downloading libwiimote, extracting. I follow these steps:

autoconf
make
sudo make install

here is the error i get in the terminal

l/include/libcwiimote-0.4.0/libcwiimote
/usr/bin/install -c -m 755 ./lib/libcwiimote.so /usr/local/lib/libcwiimote.so.0.4.0
/usr/bin/install: cannot stat `./lib/libcwiimote.so': No such file or directory
make: *** [install] Error 1

---

### Post by tictacman on 2008-01-11
problem solved.  Removed the bluetooth usb stick and tried again and it worked fine.

---

