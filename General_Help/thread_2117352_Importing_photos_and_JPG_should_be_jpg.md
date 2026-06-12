---
title: "Importing photos and JPG should be jpg"
date: 2013-02-18
forum: General Help
---

### Post by rapattack1 on 2013-02-18
Hi had heaps of trouble with importing pics from my fujifilm usb camera of late. Did have f-spot on the previous distro and now on this one. F-spot worked on the previous distro but imported as *.JPG and i need *.jpg as no site or ipload tool sees it on my hard drive unless it is lowercase which is annoying. I have to import everything into GIMP or rename. Which is crap when you have to work with lots of images. 
I noticed too that in this 12.04 environment it hasn't updated to the lates GIMP version either. I think its 2.6 or something and on the last install i had 3.2?
Shotwell i used in this new install and i don't like it plus i have to choose the camera every time rather than it auto does it when i plug in the usb cam. Also i have to rename like in the above senario.
Nautilus i tried and its ok but ofcourse not auto importing and again the rename issue.
When i did the command lsusb i got this:
```
Bus 001 Device 010: ID 04cb:021c Fuji Photo Film Co., Ltd 
```

---

### Post by dino99 on 2013-02-18
that needs to be reported

---

### Post by rapattack1 on 2013-02-18
To whom?

---

### Post by n4pgw on 2013-02-18
My experience is that I import the pictures, then I run GPrename and rename all files to lower case.  It's a pain to take this additional step, but I have some online places I can only upload lowercase extensions to.

---

### Post by rapattack1 on 2013-02-18
Oh thanks that worked a treat. Its a pain but better than renaming every file indivually

---

### Post by rnerwein on 2013-02-18
> **rapattack1 said:**
> Oh thanks that worked a treat. Its a pain but better than renaming every file indivually
hi
if you want to rename all .JPG to jpg open a terminale and run:

  rename 's/.JPG/.jpg/g' `find . -type f`
( back ticks ! around the find command)
ciao

---

### Post by rapattack1 on 2013-02-20
So that command makes every jpg from upper to lower case? Does it import files frm the camera as such? I found a year ago whatever i used to import pictures did it automatically. Wish i could remember what i used

---

