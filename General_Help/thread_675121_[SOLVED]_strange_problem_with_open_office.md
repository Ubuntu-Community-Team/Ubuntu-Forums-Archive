---
title: "[SOLVED] strange problem with open office"
date: 2008-01-22
forum: General Help
---

### Post by sandclock on 2008-01-22
HI
 recently installed ubuntu 7.04. but when i try to open any application in Open Office i get screen where it says opening and then nothing happens the opening screen disappears. Oddly this doesnt happen with evolution mail but all other apps of open office any ideas?
Regards
nik

---

### Post by LaRoza on 2008-01-22
> **sandclock said:**
> HI
 recently installed ubuntu 7.04. but when i try to open any application in Open Office i get screen where it says opening and then nothing happens the opening screen disappears. Oddly this doesnt happen with evolution mail but all other apps of open office any ideas?
Regards
nik

Type "soffice" in the terminal and post any errror you get.

---

### Post by sandclock on 2008-01-22
this is error i got 
javaldx: Could not find a Java Runtime Environment! 
thanks and regards
Nik

---

### Post by silviur on 2008-01-22
```
 sudo apt-get install java6-runtime
``` or go to synaptic package manager (Administration), Search java and choose a package.

---

### Post by sandclock on 2008-01-22
i tried 
 sudo apt-get install java6-runtime
but it kept giving me error kant find package java6 so installed it from package manager now when i run "soffice" command it doesnt give me any error. But it still doesnt start my office apps barring evolution mail 
Thanks and reagards
Nik

---

### Post by silviur on 2008-01-22
Try to start the individual Office apps from the menu, see if it works this way.

---

### Post by sandclock on 2008-01-22
Tried that
but only evolution mail opens no other apps open at all
:(
:(
thanks and reagards
Nik

---

### Post by silviur on 2008-01-22
do ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` in the Terminal console. I had a similar problem with oO, and the updates fixed it (I gave up at that moment on Openoffice, but the updates seemed to fix the problem).
Good luck!

---

### Post by sandclock on 2008-01-22
update solved it for me too
thanks a lot

---

