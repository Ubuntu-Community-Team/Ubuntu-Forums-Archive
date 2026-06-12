---
title: "run Graphical application &quot;as root&quot;"
date: 2013-09-11
forum: General Help
---

### Post by ratzepue on 2013-09-11
Hello,

I installed Ubuntu 13.04 from Ubuntu.com and I want to run the programm Eagle on it. Problem is: It is a graphical programm, and I need to start it as root, to install the license. I already tryed gksudo /opt/eagle-6.5.0/bin/eagle, but this doesn't work, because then just Firefox starts. I also tried installing nautilus-gksu, but it says, that the package isn't found. I hope someone can help me with this.
Security doesn't matter, it is a VM and not supposed to run for a long time or with important data.

Best regards

---

### Post by mastablasta on 2013-09-11
what are the install instructions for the program?

is this the program you want to install?: [http://www.kaibader.de/running-eagle-cad-6-2-on-ubuntu-12-04/](http://www.kaibader.de/running-eagle-cad-6-2-on-ubuntu-12-04/)

---

### Post by ratzepue on 2013-09-11
Yes it is this program. I downloaded it from [http://www.cadsoftusa.com/download-eagle/](http://www.cadsoftusa.com/download-eagle/) and executed the script. That is somewhat the whole given instruction, but it looks installed fine. The problem is when I start it and coose "License as freeware" I get a message "please start EAGLE as root to install the license" and I can't start it from console with gksudo, because then it says "can't open display" and when I try enter gksudo to this search field, or whatever it exactly is, it just opens firefox.

---

### Post by grahammechanical on 2013-09-11
Did you install gksu? It is not installed on 13.04 by default. Without it gksudo will not work. Appartently the developers did not think that ordinary users would want to edit system files. So, they depreciated gksu.

```
sudo apt-get install gksu
```

Regards.

---

### Post by ratzepue on 2013-09-12
Yes I did, checked it.

---

### Post by mastablasta on 2013-09-12
well it doens't say anthing about any license in that instructions.
what happens if you do 
gksu nautilus 
and then browse to the file and double click it? seems everyone mostly praises those instructions that they work....

---

### Post by QIII on 2013-09-12
Due to the original title of this thread, which I have changed, I would just like to remind everyone that explaining how to use the root account for a graphical login to a DE is not tolerated and any instructions for doing so will be jailed.  

Since I am pointing this out now, be aware that an infraction may be issued if such instructions should appear.

Please take note.

Thanks.

(mastablasta and grahammechanical -- I know you two know this, so this wasn't directed at you, rather to others who may follow ;))

---

### Post by ratzepue on 2013-09-12
I've now just installed it on an other computer and done the small documentation there. Neverless thank you all fo your ideas.

Best regards

---

