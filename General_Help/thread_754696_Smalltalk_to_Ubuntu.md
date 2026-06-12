---
title: "Smalltalk to Ubuntu"
date: 2008-04-14
forum: General Help
---

### Post by bjornsi on 2008-04-14
I am a newbie, please talk slowly.

I put my Smalltalk CD in cdrom0 and started "Install Unix". I put in my username and the Code. Then I am asked to agree the software agreement. I am asked to browse a place for my vw7.2 (Smalltalk) and I do what the Smalltalk book tells me. I browse to /usr/local/vw7.2. 

Now I get a message saying "unable to create a dirictory /usr/local/vw7.2. Permission denied ("/usr/local/vw7.2"). The box tells me that if the dirictory not exists, it will be created.

What am I doing wrong

bjornsi

---

### Post by sekinto on 2008-04-14
Root owns that directory I think, so you will have to do:
If it is a CLI install:
sudo <install file>
If it is a GUI install:
gksudo <install file>

---

