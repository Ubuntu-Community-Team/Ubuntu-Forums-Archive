---
title: "no mobile supprt?"
date: 2006-12-14
forum: General Help
---

### Post by Tekovro on 2006-12-14
i just got a new cell and i want to add mp3s but when i connect it to the usb nothing happens. doesn't show up.

phone is motorazr v3t

i just want to add some mp3's to it. is windows my only option??

---

### Post by Tekovro on 2006-12-14
i found out i need to use  a program called moto4lin but the install instructions are this:

To compile you need:
* QT Library 3.3.3 (c++ headers and binary lib)
* libusb-devel 0.8 (headers and binary lib)
* g++

Installing
========
1.  qmake
    make

2. Now you can run application.


why does installing have to be different for everything! sorry but i dont know what im supposed to do with "qmake"  is that supposed to mean something?

---

### Post by hikaricore on 2006-12-14
I'm not entirely familiar with qmake but it is most likely a compiler of some sort.  What the instructions are telling you are the commands to compile the software and what libraries you will need installed to compile it.  Every piece of software that makes up your linux operating system started out as source code, some of it gets compiled on a daily or weekly basis and it is maintained in downloadable repositories, which you might know as the Add/Remove programs feature, apt-get, or synaptic.  Each of these programs connect to different package servers and download and install precompiled software for you.  Sadly not all software is maintained in this manor as making packages for systems is time consuming.  So in these cases such as yours you will most likely need to compile it from source yourself the way it's supposed to be done.  :)

You may want to search around for "Moto4lin debian", "Moto4lin deb", or "Moto4lin ubuntu" to see if anyone is maintaining or has at one time made a package for this software.  You may still need certain libraries to run the program, but it will save you the trouble of having to compile it yourself and track down all the required development libraries.

Before you're going to be able to compile anything you'll need to get the basics, from a terminal type:

```
sudo aptitude install build-essential 
```

For everything else you're on your own unless someone else is up to walking you thought it, it's 5:30am and I'm tired lol.

---

### Post by hikaricore on 2006-12-14
One more note, not all debian packages are 100% compatible with ubuntu, but usually you can luckout and find one that works just fine.

---

