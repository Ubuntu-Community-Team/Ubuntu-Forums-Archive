---
title: "Wont load login after installing XGL"
date: 2007-01-30
forum: General Help
---

### Post by JSpencer87 on 2007-01-30
First of all i am running Ubuntu 6.10 with a 3.06 gHz Intel Celeron D 1gig ram and the ATI Radeon 9600 pro.  I installed xgl today and apparently i did something incorrectly because now when i boot up it seems that it boots the OS fine but after that it just shows a black screen with the little spinning wheel like mouse cursor and it hangs there.  I am new to linux and am proud to call myself a noob,  Any help would be greatly appreciated.  I would really like to use xgl but right now i just want to be able to use the computer.

Thanks in advance,
Justin

---

### Post by igknighted on 2007-01-30
Can you post the reply of 'fglrxinfo' and 'glxinfo | grep render'?  You could run the commands in recovery mode if you cant get to the login screen.

---

### Post by JSpencer87 on 2007-01-30
ok i have gone into recovery mode and ran the two commands you listed but both return an "unable to open display error"  What do i do now?

---

### Post by Ramses de Norre on 2007-01-30
glxinfo gives you that??
If I understand you correctly, your gdm doesn't show up no more? Then my bet is that you made a typo when creating /usr/share/xsessions/xgl.desktop.
Try deleting that file in recovery mode and see if gdm works, if so make it again and make sure you don't make typo's.

---

### Post by JSpencer87 on 2007-01-30
damn i must have really screwed this up.  I don't even see xgl.desktop all i see is gnome.desktop and xfce4.desktop

---

