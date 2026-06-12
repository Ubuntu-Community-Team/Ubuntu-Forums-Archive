---
title: "Hardy white screen after login"
date: 2008-05-01
forum: General Help
---

### Post by shakabra on 2008-05-01
I installed virtualbox.  After being prompted to restart I logged in and all i have is a white screen.  How can I recover?

---

### Post by shakabra on 2008-05-01
Any help would be much appreciated. I can open virtual terminals, but can't seem to get the GUI up and running.  I don't want to reinstall.  There must be a way to figure out what the problem is and fix it, I just don't know what it is.

---

### Post by ryanhaigh on 2008-05-01
Are you able to login via the normal GUI and THEN it goes to a white screen. If so this may be an issue with compiz/desktop effects. To get your gui back

1.login as normal, wait till the login sounds are finished allowing enough time for all your normal stuff to load (panels nautilus etc.)
2.press alt-f2 to bring up the run application dialog (obviously you won't see it but it should be there)
3.enter "metacity --replace" without the quotes and press enter

With any luck metacity should kill compiz and replace it as you window manager giving you you gui back. To make this change permanent go to system>prefs>appearance and turn of desktop effects.

---

### Post by shakabra on 2008-05-01
Thank you for your help.  This was actually a friends problem.  I tried to discourage him from reinstalling but he did it anyway.  After researching I thought compiz might be the problem.  This sounds like a very viable solution.  I'll remember it.  Nice troubleshooting.

---

### Post by Zlatko.Lakisic on 2008-05-01
is there any way to use compiz and ubuntu hardy? if not how would i downgrade back to 7.10?

---

### Post by ryanhaigh on 2008-05-01
> **Zlatko.Lakisic said:**
> is there any way to use compiz and ubuntu hardy? if not how would i downgrade back to 7.10?

Many people are using compiz successfully with hardy, if you are having an issue perhaps post back with more details such as the problem you are encountering, what your graphics card is and what drivers you are using.

---

### Post by Dybber on 2008-05-01
> **ryanhaigh said:**
> 
1.login as normal, wait till the login sounds are finished allowing enough time for all your normal stuff to load (panels nautilus etc.)
2.press alt-f2 to bring up the run application dialog (obviously you won't see it but it should be there)
3.enter "metacity --replace" without the quotes and press enter

With any luck metacity should kill compiz and replace it as you window manager giving you you gui back. To make this change permanent go to system>prefs>appearance and turn of desktop effects.

I had the same problem and the above worked to get my desktop back, but the desktop effects is already turned off, so I would have to do this on every login. Removing compiz by: ```
sudo apt-get remove "compiz*"
``` made it go away permanently.

Btw. it didn't happen in a failsafe session.

---

### Post by greyghost60 on 2008-05-01
I had the dreaded white screen too and tried everthing including reseating the graphics card. Then a brainwave. I logged in and under options found the failsafe, used it and got to the normal screen, caheck and found the accelerated graphic card driver was not in use. re-enabled it and all was fine. My grahics card is an ATI Radion X1550

---

### Post by Zlatko.Lakisic on 2008-05-02
Ok so i managed to get in using the failsafe terminal and did sudo apt-get remove "compiz*" and i remove compiz that way, but when i went to check the restricted drivers there were none on the list.

i am using an ati x1300 256mb card.

how can i re-enable compiz to work on hardy, im not sure why it wont work on hardy as it did on gutsy, seems like they took one step forward and 2 steps back....

---

### Post by Zlatko.Lakisic on 2008-05-06
anyone?

---

### Post by ryanhaigh on 2008-05-06
You can install the closed source ati driver by looking here: 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by surferkid993 on 2008-05-15
Same problem here, I have compiz still installed but I am not using it, but I really would like to. It was working fine in Gusty and now that I "upgraded" it gives me the white screen when I try and use it. I have a Radeon 9600 pro Atlantis card.

---

