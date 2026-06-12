---
title: "cdrom mount problem"
date: 2007-08-09
forum: General Help
---

### Post by dragonwings on 2007-08-09
im using ubuntu 7.04 

i can put a cdrom or dvd into disk try and it will auto mount and display what evers on the disk
thats all good 
but if i close the window and  go to " computer" the cd/dvd icon is not there this has  been like this for a while . i used to just click on the flopy icon then the cd/dvd icon would pop up
but now when i do that it pops up but when i click it it says no media mounted
so i tryed 
 sudo mount /dev/cdrom /media/cdrom0
to mount it but it said media is allready mounted

:confused:

---

### Post by lisati on 2007-08-09
The term "my computer" is more usually associated with Windows. Are you able to find your disk drive when you go to "computer" on the "places" menu?

---

### Post by dragonwings on 2007-08-09
my computer /computer  is what i meant  i dont have windows installed and i dont have wine or anything like it 

just ubuntu 7.04

typeoooo sorry dude

---

### Post by dragonwings on 2007-08-09
any ideas

---

### Post by dragonwings on 2007-08-10
anyone out there????

---

### Post by dragonwings on 2007-08-11
sos

---

### Post by dragonwings on 2007-08-20
is anyone out there ?????

---

### Post by Cubells on 2007-09-04
Can you paste the output of these commands when you put the cdrom into disk try?

$ cat /etc/fstab

$ cat /etc/mtab

Cheers...

---

### Post by vanadium on 2007-09-04
I recently also experienced a similar issue, where an inserted DVD would not automatically mount. I could mount it manually, though.

---

