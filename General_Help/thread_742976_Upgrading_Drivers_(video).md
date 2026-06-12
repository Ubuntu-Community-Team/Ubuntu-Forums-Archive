---
title: "Upgrading Drivers (video)"
date: 2008-04-02
forum: General Help
---

### Post by Papa Smurf on 2008-04-02
I have installed Ubuntu 7.10 as my VERY first Linux system. It was VERY easy to install and I liked the simplicity but, I have come to an impasse. I would like to upgrade the video driver for my ATI 9550 card and change the bus the system is saying it is on. It is an AGP card with 256mb and the system is reporting it as a PCI card.

Maybe it is old hand to you guys but this is a major learning curve for me. The package I downloaded is a .run one and I can't seem to activate it? Any help would be most welcomed :D

---

### Post by justleen on 2008-04-02
AGP would list as PCI as well , that is just fine.
```
 lspci |grep -i agp 
```
to run the .run package, you have to make sure it is execuatable
```
 chmod a+x *.run 
``` that will make it executable.

afterthat you can run it as 
```
 ./atidriver.run
```

edit: this is all executed from a terminal... Applications> Terminal

---

### Post by Papa Smurf on 2008-04-05
Thanks very much for coming to my aid. I will let you know how I go. :)

---

