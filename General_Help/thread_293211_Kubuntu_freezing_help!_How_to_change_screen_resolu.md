---
title: "Kubuntu freezing help! How to change screen resolution manually."
date: 2006-11-04
forum: General Help
---

### Post by mag27 on 2006-11-04
hi,

So i changed my screen resolution.  Then, i was pasting something into word and my computer frooze and I had to restart it.  I get past everything, boot-up, all the starting, scanning "o.k." stuff and then right before login it freezes, no error message, just all those o.k. messeges as normal, then a black screen with a cursor in the top left corner, then to the black screen with the kubuntu blue logo. 

So I tried root@michelle:@ kdesu kate /etc/X11/xorg.conf to manual change the screen resolution but it's saying that it can't connect to "X server"  
I tried startx and got a big log which states two errors: (EE) ATI (0): virtual size (2048x1536) exceeds video memory. *<-oops guess i went overboard with the screen res.*
(EE) sceen(s) found but .....something like there not right to load on.  so then i tried to do the whole kdesu kate /etc/ thing but it still says not connected to server.  I'm so confused.  Thanks for whatever help you can give!


Please help ASAP I have an essay on that computer that needs to get out tonight (I know, I should have backed up.....:_( 

Thanks so much!
Michelle

---

### Post by mag27 on 2006-11-04
above updated to show my ""progress""

---

### Post by der_joachim on 2006-11-05
```
sudo dpkg-reconfigure xserver-xorg
``` should at least enable you to get a simple, non 3D accelerated desktop.

---

### Post by reldruH on 2006-11-05
> **mag27 said:**
> (EE) sceen(s) found but .....something like there not right to load on.  so then i tried to do the whole kdesu kate /etc/ thing but it still says not connected to server.

From the command line, trying using nano instead of kate. It's a basic cli text editor that's useful when X isn't working.```
sudo nano /etc/X11/xorg.conf
``` should let you edit your xorg file, and check if your essay is still there as long as you know where you saved it to. kate is a graphical text editor and won't run without X. nano will :-)

Hope that helps.

---

