---
title: "Grub boot off usb drive?"
date: 2007-11-12
forum: General Help
---

### Post by kdarkentity on 2007-11-12
Out of curiosity Lets just say i have an operating system on my usb drive, could i add an entry to the grub boot list for a usb drive? And yes i already know i could use my bios to do this.

---

### Post by meierfra on 2007-11-12
Yes, it can be done fairly easily. If you need help, let us know the specifics.

---

### Post by kdarkentity on 2007-11-12
oh wow thats amazing, well all i need to know is what i put in for the location of the usb drive? i mean for a hard drive i would put in something like (hd0,1) but what would that be for a usb drive?

---

### Post by meierfra on 2007-11-12
It would be something like (hd1,0).  Grub starts counting at zero:

(hd0,0) first partition on the first hard drive
(hd0,1) second partition on the first hard drive.
(hd1,0) first partition on the second hard drive
...
(hd5,11) 12th partition on the sixth hard drive and so on

---

### Post by kdarkentity on 2007-11-12
ahh i see , i just ordered am 8gb usb drive and i was planning on running ubuntu off of it as i have in the past soo i will let you know how that goes. Thanks

---

