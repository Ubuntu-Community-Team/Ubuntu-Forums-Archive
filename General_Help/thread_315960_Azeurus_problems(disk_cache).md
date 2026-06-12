---
title: "Azeurus problems(disk cache)"
date: 2006-12-10
forum: General Help
---

### Post by James- on 2006-12-10
My azeurus is working fine, just that I cannot change the disk cache size(is currently set @ 1MB (not alot...)) I was wondering how to raise it, because before I upgraded to edgy(i have 6.06) I was able to set it to 20MBs. Please help :(

---

### Post by James- on 2006-12-10
anyone?

---

### Post by bscbrit on 2006-12-10
James-, have patience waiting for a reply.  I am just getting out of bed because I cannot spend 24 hours a day on the computer.  Secondly, if nobody replies it might be because nobody yet knows the answer to the question.  But don't worry, like me they will be trying to solve the problem and will reply to you as soon as they have the answer.  ;)

---

### Post by bscbrit on 2006-12-10
In Azureus, go to Options -> Files -> Performance Options and ensure that 'Enable disk cache' is ticked, and that you have set the size of the cache that you want to use.  :-D

---

### Post by bscbrit on 2006-12-10
Ah, I see what you mean.  Azureus is not allowing you to set a cache size.  That's a bug - report it please.

---

### Post by Izkata on 2006-12-18
I had it working correctly when I first got Azureus on Edgy - I think it was with the 2.5.0.1 Beta version - but I "downgraded" to the non-Beta 2.5.0.0 and now see the problem.

EDIT:  Duh.  Found it:

[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

And yes, it is fixed in this build.

EDIT2:  Well, you can change the number in 2.5.0.1, and save it.  But it gets reset back to 1 MB upon restarting Azureus, and doesn't seem to actually affect the cache.

---

### Post by Izkata on 2006-12-18
I'm making a new post because I feel this deserves a bump.

I'm currently on Azureus 2.5.0.1_B40, and followed the instructions at [http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html) to update my version of Java.

Both the Cache Size problem mentioned above, as well as a UPnP problem I've been having (unable to initialize SSDP) were fixed, no problems.

As an amusing side-note, Azureus no longer claims I have 8 Exabytes of virtual memory!  :mrgreen:

---

