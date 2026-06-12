---
title: "restore ubuntu to stable state"
date: 2004-11-18
forum: General Help
---

### Post by puzzledm on 2004-11-18
After trying out a few things I have now found that my system won't start X properly.  Also when I try to re-install Ubunutu-desktop synaptic turns itself off.  And a few other idisoyncracies are also happening.

How can I restore my system to it's state just after I installed but also keep the programs I have installed and the files I have in my Home file?

Or is there a way of running a program which checks the consistency of my system and tells me where/ how to fix problems?

Also how do I get X to start properly again?

---

### Post by scoon on 2004-11-18
Hey there, 

ubuntu uses apt to manage its packages.  Take a look at man apt-get for some ideas.

First I would try apt-get check and see if any packages are broken.

Also, what were the "few things" that you tried that broke your system?

scoon

---

### Post by jdong on 2004-11-18
exactly what did you do? What is the output from **startx**?

---

### Post by puzzledm on 2004-11-18
I updated to firefox 1 in the hoary rep's by changing warty to hoary in the apt.sources.list and then changing them back. I also installed totem-xine which removed ubuntu-desktop.  And when updating to firefox 1 in hoary I agreed to the installation or upgrade of the dependencies.

I think the start problem is with GDM not X - when it gets to the stage in boot where it starts GDM the cursor appears and then a screen pops up saying 'I can not start x on this desktop as it is all ready running would you like me to start it elsewhere' or somthing along those lines.

In Synaptic -> Status -> broken or locally installed, there are lots of programs I didn't install would it help removing them?

---

### Post by rbrimhall on 2004-11-18
Did you upgrade X11 fro Xfree86 to Xorg? Firefox should have had only one dependency AFAIk which is libpng >= 1.27 (based on the d=Debian proper package)... if you installed a lot of dependencies then you may be running hoary now.

---

### Post by puzzledm on 2004-11-18
I may have done - is the best thing at this stage to upgrade fully to hoary or to somehow (help required) downgrade back to Warty?

---

### Post by Screw on 2004-11-18
I had same problem. Just do *apt-get install gdm *    from hoary main. This helped me

---

### Post by puzzledm on 2004-11-18
I am just going for a complete upgrade to Hoary ... the worse that can happen is that I have to reinstall ubuntu from CD and somehow backup my files through the live CD or something ... here goes!

going to use ....

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

---

### Post by puzzledm on 2004-11-19
The upgrade to hoary went fine and fixed all the problems - I am a bit worried that I now have unstable versions of everything!

Is there a way if I want to change the repositories back to Warty and downgrade everything back to warty?  Could I run apt-get dist-upgrade to warty?? :?

---

