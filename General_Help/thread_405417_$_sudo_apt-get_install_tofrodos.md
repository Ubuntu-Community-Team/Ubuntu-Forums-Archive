---
title: "$ sudo apt-get install tofrodos"
date: 2007-04-09
forum: General Help
---

### Post by Sup3rkirby on 2007-04-09
```
$ sudo apt-get install tofrodos
```
This code will not work for me.  It says it can not find the 'tofrodos' package.  I NEED this package so that I can install it and get something working.

I have tried loading the cd to find the package and it isn't there.  Is there somewhere I can download the package? how would i install it then?

I really need help here and as soon as possible please.

---

### Post by taurus on 2007-04-09
Did you enable both universe and multiverse in /etc/apt/sources.list?  Open a terminal and edit /etc/apt/sources.list

```
gksudo mousepad /etc/apt/sources.list
```
and remove the # in front of all the lines with **deb** at the beginning.  Then, save it and run

```
sudo aptitude update
sudo aptitude install tofrodos
```

---

