---
title: "Confusion about Xgl...Compiz"
date: 2006-11-03
forum: General Help
---

### Post by krypto_wizard on 2006-11-03
Hi,

I am overwhelmed with the information and different threads about xgl ..aixgl and compiz anf beryl. 


Can somebody explain why variuous technologies are used for eye candy ?

Which one is good and for which hardware. 

Is there any idiots guide for this.

Can somebody please simplify all the different solutions and tell one generic thing to do.

Thanks

---

### Post by moffa on 2006-11-03
Xgl is an X server architecture designed to take advantage of modern graphics cards via their OpenGL drivers, layered on top of OpenGL via glitz. (wikipedia)

Compiz is one of the first compositing window managers for the X Window System that is able to take advantage of OpenGL-acceleration. The integration allows it to perform compositing effects in window management, such as a minimization effect and a cube workspace.

Nvidia cards have better support in Linux therefore they are "better"
Just follow one of the guides below to set it up
This thread has all the ways to get xgl etc [http://ubuntuforums.org/showthread.php?t=272104]("http://ubuntuforums.org/showthread.php?t=272104")

---

### Post by igknighted on 2006-11-03
There is a sticky at the top of this forum that has all the information you would ever want, but let me throw my two cents in to point you in the right direction.  AIGLX and XGL are both ways of creating a 3D desktop environment.  In ubuntu 6.10, AIGLX is built into the OS, so it is the easiest and least invasive way to get the 3D eye candy.  This will work with almost any nvidia graphics card, I believe almost any Intel card, and (in theory) any ATI card up to the x800 (if your card isn't x1000-x1900, try aiglx first)  With aiglx you can run 3D software (like google earth) at the same time.  XGL is the original means of creating a 3D desktop environment, but it is very invasive and if something is wrong your system could be left seriously damaged.  I would recommend XGL only if you have an ATI card that cannot use aiglx.  As far as beryl and compiz, compiz is the original desktop and beryl is a fork from that project.  Right now I would say beryl is a little further along, and it is a more pleasant experience, but either one should work perfectly fine.  Hope this helps, read the sticky on top for specific information if you decide to try it out.

---

### Post by TigerWolf on 2006-11-03
Just a quick note, if you plan to use wine or cedega you will temporarily have to turn off beryl.

---

### Post by _simon_ on 2006-11-03
> **TigerWolf said:**
> Just a quick note, if you plan to use wine or cedega you will temporarily have to turn off beryl.

Not if you use AIGLX. 

If you use XGL then there is a workaround.

---

### Post by elettronicha on 2006-11-03
> **krypto_wizard said:**
> Hi,
I am overwhelmed with the information and different threads about xgl ..aixgl and compiz anf beryl. 
Can somebody explain why variuous technologies are used for eye candy ?
Which one is good and for which hardware. 
Is there any idiots guide for this.
Can somebody please simplify all the different solutions and tell one generic thing to do.
Thanks



I quote myself once, if it can be helpful:
> As far as I know, technically:

1.
-Xgl is a Xorg fork, which replaces the whole X server
-Aiglx is a Xorg extension and can be (un)loaded as your wishes

2.
-Xgl is supported by Novell
-Aiglx is supported by everyone

3.
-Xgl delegates some functions to Mesa libraries and doesn't require drivers (often proprietary) supporting specific extensions
-Aiglx delegates everything to drivers, so driver and video card role are central matters

4.
-Xgl runs upon a runnign X server, so two graphical servers are running in the same moment
-Aiglx is a simple extension and doesn't weigh down X


[Here it is the link]("http://ubuntuforums.org/showthread.php?t=288620") to a thread I opened, there are tons of discussion indeed in the fora. And a couple of guides I found OK are [here]("https://help.ubuntu.com/community/BerylOnEdgy") and [here]("http://wiki.beryl-project.org/index.php/Main_Page"). Find yourself the difference between Compiz and Beryl in the relative homepages or try a search in wikipedia.

---

