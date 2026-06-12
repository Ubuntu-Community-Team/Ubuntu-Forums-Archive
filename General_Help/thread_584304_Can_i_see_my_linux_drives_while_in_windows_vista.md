---
title: "Can i see my linux drives while in windows vista?"
date: 2007-10-20
forum: General Help
---

### Post by kdarkentity on 2007-10-20
I realize this is better suited on a windows forum but ill ask here anyways, is it possible for me to see my ext 3 file systems  while booted into windows vista?

---

### Post by rbmorse on 2007-10-20
no

---

### Post by chrishere01 on 2007-10-20
yea ik it sux
you cant
but i just save everything to a flash drive anyways

---

### Post by ihcnet on 2007-10-20
Yes, you can see the drives, but you need the help of another program. The program is found here [http://fs-driver.org/](http://fs-driver.org/) and you might have to run it with the compatibility mode set to Windows XP. I've had great experiences with it in XP and Vista. Good luck.

---

### Post by kdarkentity on 2007-10-20
ok thanks, i installed the driver and "IFS Drives" was added to my control panel but whenever i try to open it , it just crashes, gotta love windows huh... lol

---

### Post by kdarkentity on 2007-10-21
Absolutely amazing!, it did work! now i can see my linux drives from my computer!

---

### Post by mahousaru on 2007-10-21
> **kdarkentity said:**
> Absolutely amazing!, it did work! now i can see my linux drives from my computer!

If you are using the IFS ext2 drivers for the love of {insert valuable item here} be careful about UTF8 file names.  The driver can only use the system default and will trash your files if you copy them over.  For example if you do a file move of Chinese named files the files will appear as ???.jpg, ????.jpg etc etc.

---

