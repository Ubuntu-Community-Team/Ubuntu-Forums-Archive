---
title: "GRUB error! Pleas help!"
date: 2007-08-26
forum: General Help
---

### Post by WRyder on 2007-08-26
earlier today, i deleted the portion with ubuntu on it and extended the portion with windows vista. after a computer restart, i keep getting the text, grub loading error 17. i tried to load the ubuntu live disk and the windows disk but they wont even load. what do i do?!

---

### Post by jamvegan on 2007-08-26
The first, very small, stage of GRUB is stored in the master boot record, but the information that GRUB needs to actually boot any operating systems is stored in /boot/grub, which you deleted along with the rest of Ubuntu.  You need to restore the Windows bootloader to the MBR, which I believe that you can do with your Vista CD.  Unfortunately, I have no experience with Vista, so hopefully either there is some obvious restore function when you boot into the CD, or someone who's familiar with Vista will offer further instructions.  Good luck!

---

### Post by WRyder on 2007-08-26
thanks but i cannot boot off of any cd!

---

### Post by jamvegan on 2007-08-26
Hm.  Do you get a grub> prompt after the error message? If so, try the following:
```
grub> root            (hd0,0)
grub> savedefault
grub> makeactive
grub> chainloader     +1
```
You may need to change the first line.  hd0,0 refers to the first partition of the first IDE drive.
If that enables you to boot Vista, then follow the instructions found [here]("http://support.microsoft.com/kb/919529") to restore your MBR.

---

### Post by WRyder on 2007-08-26
i didn't...

---

### Post by jamvegan on 2007-08-26
Why can't you boot from a CD?  Do you not have a CD drive, does your CD drive not work, or do you have a working CD drive which your computer will not boot from?

---

### Post by WRyder on 2007-08-26
everything is fine. for some reason, when i put the cd in and then choose to boot from a cd, it just shows a blank screen and then shows the error message.

---

