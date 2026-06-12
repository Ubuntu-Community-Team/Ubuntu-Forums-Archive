---
title: "question on disc drive"
date: 2006-11-07
forum: General Help
---

### Post by UchihanoKonoha on 2006-11-07
I was recently trying to install WOW on my system and when it prompted to insert WOW disc 2 I could not eject disc 1 and so i tried my other drive but it did not want to read my second drive is, then i right clicked the disc drive on the desktop and clicked eject and the following message displayed:

> 
Unable to eject media

^show details

**Details**
> 
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed


based on this what should i do to fix the problem im still sitting here in the middle of installation, I dont want this to happen again is there a way to remedy the problem so i dont have to cancel installation and is there a way to keep this from happening again. Give me some suggestions please
Thanks :-D

---

### Post by Atomic Dog on 2006-11-07
I had a bad disc give the same message.  Try reburning the discs at a lower speed and verify the written data (if you can) and try again.

---

### Post by UchihanoKonoha on 2006-11-07
Im not talking about burning im talking about cd-rom installation

---

### Post by galileon on 2006-11-07
try unount -l ....(thats a small L)


its called lazy unmount and unmounts pretty much anything...

---

### Post by UchihanoKonoha on 2006-11-07
when i tried that this message appeared

>  
Usage: umount [-hV]
       umount -a [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
       umount [-f] [-r] [-n] [-v] special | node...


---

### Post by galileon on 2006-11-07
sorry, i shud have been more explicit, i meant:

sudo umount /media/cdrom0 -l

---

