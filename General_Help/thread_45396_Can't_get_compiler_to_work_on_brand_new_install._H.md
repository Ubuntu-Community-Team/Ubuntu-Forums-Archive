---
title: "Can't get compiler to work on brand new install. How to do it?"
date: 2005-06-29
forum: General Help
---

### Post by Circlotron on 2005-06-29
Hi all.
I just installed Hoary Hedgehog last night (what a *painless* install!!!) and pretty much everything seems to be right, but I cannot get the compiler to do anything. Specifically, I wanted to compile KDE which I have accomplished before on other distro's. What I have read, it seems that gcc is not enabled somehow by default. Could someone please direct me to where I could find out how to fix this? 

	TIA.  :-)

---

### Post by SGC on 2005-06-29
To install gcc, g++, and make, run this command:
```
sudo apt-get install build-essential
```

Or this one:
```
sudo apt-get install gcc
```

There is no need to compile kde, you can install the latest version with apt-get, add **one** of this lines to /etc/apt/sources.list
```
deb http://kubuntu.org/hoary-kde341 hoary-updates main
deb http://download.kde.org/stable/3.4.1/kubuntu hoary-updates main
```

Then:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by Circlotron on 2005-06-30
[QUOTE=SGC]There is no need to compile kde *snip* [/QUOTE]
I know, thanks :-) I just want the satisfaction of doing it, particularly so I can set the compiler options a bit more aggressively. 

OK. Looks like gcc has downloaded.  \\:D/  Thanks heaps.

---

