---
title: "VMware Tools"
date: 2005-10-17
forum: General Help
---

### Post by BKnight on 2005-10-17
I have installed Ubuntu 5.10 into a VMware under Windows so I can try to get a grasp on Linux and learn to love it as much as many of you already do. I have lots of questions already but my most immediate one is where to find the "make" file on the standard CD installed version. I want to install the VMware Tools to take advantage of the advanced features of VMware but I am getting stuck at this point of the install:


Setup is unable to find the "make" program on your machine.  Please make sure it is installed.  Do you want to specify the lcoation of the program by hand?
[yes]

What is the location of the "make" program on your machine? 


It wants to complete name of the binary file but a quick search of the system and I can not find that file. I am assuming that it is not installed by default but I do not know how to go about installing either. Any assistance would be greatly appreciated. Please remember, answers will best be understood as though you were explaining it to your grandmother. :p

---

### Post by KingBahamut on 2005-10-17
sudo apt-get install build-essential from a terminal command line.

---

### Post by cosulliv on 2005-10-17
There was/is an excellent VMware install guide for Breezy (GCC 4 not being compat with whats required.)

[http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=65638&highlight=vmware)

Have a go...
c.

---

