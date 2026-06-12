---
title: "How to install opennms"
date: 2013-01-10
forum: General Help
---

### Post by taurai on 2013-01-10
I have installed ubuntu 12.04 and need  to install opennms. The  directions say I should  create a file called "opennms.list" within the "/etc/apt/sources.list.d" directory, with the following contents:   # contents of /etc/apt/sources.list.d/opennms.list  deb [http://debian.opennms.org](http://debian.opennms.org) ***stable*** main  deb-src [http://debian.opennms.org](http://debian.opennms.org) ***stable*** main

how do I create the said fil

---

### Post by mlentink on 2013-01-10
Open up gedit, copy and paste the text in it and save it under that name



...easy

---

### Post by Cheesemill on 2013-01-10
First open the file for editing using gedit with root privileges by opening a terminal and typing...
```
gksudo gedit /etc/apt/sources.list.d/opennms.list
```
Then type the following 2 lines into the blank document...
```
deb http://debian.opennms.org stable main
deb-src http://debian.opennms.org stable main
```
Then just save the file and close gedit.

---

