---
title: "Xserver crashing NMI error - T60 laptop"
date: 2007-02-05
forum: General Help
---

### Post by IndigoMontoya on 2007-02-05
I am having a strange problem with my laptop.  I have found that when I leave my laptop on for a  period (and leave - it never happens when I am around - of course) my xserver seems to crash (it is at the login screen.  I am running an up-to-date edgy with beryl on an ibm T60 with an ATI video card.  One time it occurred I had another virtual terminal open and I received the error message:

```
Uhhuh. NMI received. Dazed and confused, but trying to continue
You probably have a hardware problem with your RAM chips

```

With some numbers associated (I copied the exact message from the web). 

a link to my /var/log/Xorg.0.log is [here]("http://missionclear.com/upload/Xorg.0.log") (I could not upload it because of size restrictions to this forum.

 I have since run memtest86+ and had over 80 passes with no errors.  Also, this computer is an XP dual boot.  I rarely use it, but have never had a problem when in windows.  For no good reason I feel the problem may be with the fglrx driver.  Any thoughts?  Please.....

---

### Post by jazzman76 on 2007-03-26
I have the same issue on my laptop. :-(
I have a Thinkpad r60 with a ATI X1400 card running the latest fglrx driver. I have searched alot on different forums, but as of now have not found any solution to the problem. My laptop locks up, but I'm able to move the cursor. I have tried several configurations of xorg.conf, but have yet to find one that works. I have installed a additional RAM chip in my PC, and I'm now considering removing it to see if that solves the problem. 
If anyone have seen this problem, or can provide any info on the NMI received message, please help out.
Thanks

---

### Post by releehw on 2007-04-27
I have a T60 on which I'm running Feisty-beta with Beryl .20 and I see the same thing. The 'dazed' message appears one or more times before an X11 crash, usually at about the 2 hour mark.  I suspect this has to do with Beryl, and not fgrlx, as I can run gnome using the fglrx driver without the X11 crashes.  I'm also able to run Mepis using fglrx with no problem (Mepis uses the Ubuntu package repository). The suggestion in the 'dazed' messages that there is a hardware malfunction is probably bogus, since, I don't see this in the absence of Beryl.   

A solution would be nice but, in the meantime, I'm just doing without Beryl...

---

### Post by jazzman76 on 2007-04-29
Hmmm...
I'm having problems in Gnome with regular X. I even have problems with the feisty live CD. I tried with another R60, and on this PC it seemed to work. I'm going to fine more reference test PC's.

---

