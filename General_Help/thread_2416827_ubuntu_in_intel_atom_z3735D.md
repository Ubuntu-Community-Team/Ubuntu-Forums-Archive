---
title: "ubuntu in intel atom z3735D?"
date: 2019-04-16
forum: General Help
---

### Post by jhay2 on 2019-04-16
Hi ,
I am ubuntu lover , and hoping that the ubuntu will support the intel tablet like mine

i have a cherry mobile alpha play tablet it is a tablet made in philippines
the Specification for this device is stated here
[https://mobilespecs.net/tablet/Cherry_Mobile/Cherry_Mobile_Alpha_Play.html](https://mobilespecs.net/tablet/Cherry_Mobile/Cherry_Mobile_Alpha_Play.html)


[LIST]
[*]Intel Atom Z3735D, 1.33 GHz Quad Core Processor
[*]Intel HD Graphics - Gen 7 GPU
[*]1 GB RAM, 16 GB ROM and microSD expandable up to 64 GB
[*]8.0 inch HD IPS Capacitive Full Touch Screen with Multi touch
[*]Dual Camera, 5 MP Rear and 2 MP on Front
[/LIST]

already installed ubuntu 16.04 linuxium version 

yes this version works but there are some unsolved problems

WIFI (always disconnected in random time)  needs to unload and reload the rtx modules to work again
battery is not detected 

camera is not working


hope that this fix soon 

thank you

---

### Post by jhay2 on 2019-04-16
Thread bump , thanks . need this

---

### Post by mörgæs on 2019-04-20
How does it behave in a fresh install (no upgrades) of 18.04 or 19.04?

---

### Post by jhay2 on 2019-04-28
hi thank you for the reply . i've already tried the original 18.04 ( not linuxium)   it can boot but theres problem , wifi not working, camera not working , bluetooth not working , when in sleep mode/ hibernate mode it will stays there when i try to unsleep using hardware buttons.   volume keys not working . battery not detected.

---

### Post by mörgæs on 2019-04-30
A lot of problems... You probably need to focus on one at a time. Which of them is most important to you?

Also it would help to see the hardware details (even though you have posted the link in original post). Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post the contents of lshw.txt in CODE tags.

---

