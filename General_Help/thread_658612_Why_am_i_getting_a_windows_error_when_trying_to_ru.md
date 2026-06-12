---
title: "Why am i getting a windows error when trying to run linux?"
date: 2008-01-04
forum: General Help
---

### Post by hotroddude on 2008-01-04
Hi, this happened yesterday. I was changing some of my compiz settings and then outa nowhere it just froze up, i was like ok ill just restart compiz, nothing happened so i restarted the system. Im getting the weirdest error when i start it up, its a windows message???? take a look


[IMG]http://Steven-hotroddude.smugmug.com/photos/239724440-L.jpg[/IMG]

whats up with that? i installed gutsy gibbon with wubi since i couldnt get my computer to run off the live cd i made. i figure im going to need to reformat but is there a way i can manage to save all the repos i had and my files/awn/all the other custumized stuff through wubi? does the save iso file option keep all that? all help on this weird subject is highly appreciated.
thanks in advance.
-steven

---

### Post by Sef on 2008-01-04
Moved to the wubi forum.

---

### Post by hotroddude on 2008-01-04
> **Sef said:**
> Moved to the wubi forum.

thanks, i didnt know there was a wubi forum here.

---

### Post by ago on 2008-01-05
Run 

chkdsk /r

from a windows CD or using a repair ISO available on the web

---

### Post by hotroddude on 2008-01-05
> **ago said:**
> Run 

chkdsk /r

from a windows CD or using a repair ISO available on the web

can you link me to a repair iso? and how do i run it?

thanks for helping!

-steven

---

### Post by ago on 2008-01-07
You can use the original windows CD (or borrow one)

All you have to do is boot with the CD in, when given the option press "r" to get to the recovery console, then type

chkdsk /r

If you installed on the d: drive, change to d: before giving the command above.

As for non MS iso's you can google for "windows recovery console iso". For instance [http://www.thecomputerparamedic.com/files/rc.iso](http://www.thecomputerparamedic.com/files/rc.iso) . I haven't used that myself though. You will have to create a  bootable CD from the iso in this case.

---

