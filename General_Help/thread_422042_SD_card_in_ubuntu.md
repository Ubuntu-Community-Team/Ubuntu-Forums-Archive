---
title: "SD card in ubuntu"
date: 2007-04-24
forum: General Help
---

### Post by Colonial_Red on 2007-04-24
Can anyone tell me how I can format an SD card? In windows I just have to right mouse click and select format. How do I do this in ubuntu?

---

### Post by GuitarRocker2562 on 2007-04-24
are you a noob? cause if you are you may format your HDD by accident, let me try to find a program

---

### Post by Azakus on 2007-04-24
Easiest way is like this:
Install Gparted from the repositories (sudo aptitude install gparted)
Then, open gparted and find the card (something like /dev/sdX), should be listed as "unallocated"
Click Partition -> New and format as FAT16.

---

### Post by GuitarRocker2562 on 2007-04-24
does it need to be formated, or erased?

---

### Post by Colonial_Red on 2007-04-24
The fear of accidentally formatting my hard drive is precisely why I'm asking ehre first before touching anything. 

Thanks for the responses, I'll try that.

---

### Post by GuitarRocker2562 on 2007-04-24
Oh, any like triple check to make sure you are selecting your card (the smaller one)

---

