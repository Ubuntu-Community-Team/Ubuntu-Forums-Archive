---
title: "How do i install wine?"
date: 2007-01-28
forum: General Help
---

### Post by naruto650 on 2007-01-28
Im new at this linux thing. I was wondering how you can install wine on ubuntu? Im running on dapper.

---

### Post by r4ik on 2007-01-28
Try,

[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

Good luck !

---

### Post by agustin.g on 2007-01-28
The simplest way to install it is with Automatix.

just [COLOR="Red"][Clickety Here](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)[/COLOR] to see the installation instructions. After that just open up Automatix (be sure to give the administrator password) and check the box next to "Wine", then click on "start"

hope that helps

Edit: sorry r4ik, just stepped on your toes

---

### Post by r4ik on 2007-01-28
Nevermind :)

---

### Post by ssavelan on 2007-02-13
open a terminal and type (or paste from here):

sudo apt-get install wine

then, you probably want to run:

winecfg

---

### Post by dcstar on 2007-02-14
And if you ever make a mess of your **wine** configuration and want to start afresh, just rename (or delete) the hidden **.wine** directory in your home folder.

Reinstalling the **wine** package doesn't do anything to any configuration you may have already built.

---

