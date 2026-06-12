---
title: "I dont have  1024*768 resolution in Xubuntu"
date: 2008-06-27
forum: General Help
---

### Post by khajavi on 2008-06-27
when I install Ubuntu(gnome) I can set my resolution to 1024*768
But in xubuntu I dont have this option and in my resolution list in Display setting there are low resolution
what should I do

when I go to reswtricted driver I have nvidia-legacy in red color.

how can I fix this problem?

---

### Post by nikgare on 2008-06-27
Can you tell us which graphic card you have?

---

### Post by khajavi on 2008-06-27
My nvida graphic card is ver very old
It is TNT2 64 
But I know that this graphic card support this resolution

---

### Post by nikgare on 2008-06-27
If you run thos command in a terminal:

sudo displayconfig-gtk

Are your graphic card and monitor being corectly identified?

---

### Post by ubuntu-freak on 2008-06-29
The above command should really be "gksudo displayconfig-gtk". Also, see if this command sets your resolution:
 
**sudo xrandr -s 1024x768**
 
If it doesn't, try selecting the "generic" monitor type in displayconfig-gtk instead of "default".

---

### Post by untermensch on 2008-06-29
Have you tried rebooting? The other day I had the same problem, and after I got to ticked off I turned off the computer. later I went to turn it on and it had the resolution option =]

---

