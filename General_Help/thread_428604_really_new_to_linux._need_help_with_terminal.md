---
title: "really new to linux. need help with terminal"
date: 2007-04-30
forum: General Help
---

### Post by Ndonato on 2007-04-30
alright so i'm trying to install the flash player 9 for firefox and I need to know how to change what directory i'm in while using the terminal.

---

### Post by ola on 2007-04-30
To change directory to the directory "directoryName" you use

cd directoryName

To change directory to the directory "/home" you use

cd /home

To change directory to one level closer to the root you use

cd ..

Good luck!

---

### Post by aysiu on 2007-04-30
This will help you get Flash installed:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by zvacet on 2007-04-30
[http://linuxcommand.org/]("http://linuxcommand.org/")

---

### Post by Nythain on 2007-04-30
dont forget that the ~ is commonly used to replace /home/you... ie cd ~ will take you to your home folder... and being located at somewhere like ~/Desktop would mean the desktop of your home folder... also a nifty note... spaces can be represented with the \ then the space... like the example of cd ~/.wine/drive_c/Program\ Files would take you to /home/you/.wine/drive_c/Program Files... wich brings me to another point... hidden files and folders are illustrated with a . in front of them and can be seen using ls -a in the terminal

---

