---
title: "root privilages - can i search a folder and edit it?"
date: 2007-11-23
forum: General Help
---

### Post by mattgaunt on 2007-11-23
Hey everyone

I am the only person who uses my computer, i am assuming i am the root user under ubuntu.

I want to be able to search throught my directory and be able to copy and paste some fonts straight into my fonts truetype folder, but it doesnt let me, and i will have a go with the command line - but i jus prefer the ease of just doing it using windows.

Is there anyway i can get round this just temporarily when i need to - i know its a gd thing all rnd cos then i won't screw anythin up but jus when i want to make a minor change it wud be great

Gaunt

---

### Post by taurus on 2007-11-23
<Alt>F2 -> gksudo nautilus

---

### Post by hellion0 on 2007-11-23
You'll need to either use...
```
su -
```...to log into the root account itself (if you've enabled one) OR type "sudo" before using the commands. (For example, "sudo cp path/to.file new/path") (The password for YOUR user account will be required for sudo.) If you're trying to do this with the GUI, try...
```
gksudo nautilus
```...to open a window that will allow you to graphically move files around, but with root privs.

---

### Post by mattgaunt on 2007-11-23
Yeah i just wanted to do it with the GUI im not biggest fan of using the command line for all that sorta stuff and didnt know u cud use su root for ubuntu so ill give that a go and see if that works, but thanks for the help

You've made me a very happy man

:-P

Gaunt

---

