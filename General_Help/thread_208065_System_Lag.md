---
title: "System Lag"
date: 2006-07-02
forum: General Help
---

### Post by jperez on 2006-07-02
Hello all!

I just upgraded to Breezy Badger earlier today.  Now, I've had this problem since Hoary Hedgehog.  The system will periodically lag for no reason.  Has anyone experienced this before?  Does anyone have a solution?  Here are my system specs:

[b]Dell Inspiron 8100 Laptop
CPU: Intel P3m 1Ghz/733Mhz SpeedStep
Memory: 256 RAM
Dual Boot: Windows XP Home and Ubuntu - Breezy Badger[/b]

Now, I've installed Ubuntu (Hoary Hedgehog) on a PC sometime back that had 256MB of RAM and a 600Mhz AMD Anthlon Processor and it never lagged.  I hope someone can help me.  Thanks!

Jesse~

---

### Post by encompass on 2006-07-03
it could be an issue with your processor type.  some p3 I have seen with issues like what you are saying.
check your kernel and make sure your running the 686 instead of the 386 version.
Additionally, you may like to clean install the system.  and see if that helps.
Lastly, why don't you try dapper drake, it is very stable.

---

### Post by jperez on 2006-07-03
Well, how do I know if I'm using the 686 or 386 version?  I'm very new with Linux but am learning very fast.  Also, I'm trying to not have to reinstall the system.  Also, I already placed a shipment for 10 CD's of 6.06 Dapper Drake but it will take some time to get here as I ordered them about 2 days ago.  Anyway, thanks for the speedy reply.

Jesse~

---

### Post by encompass on 2006-07-03
99 percent of the time you don't have to reinstall... I don't have to anymore, but thats cause I know what I am doing.
as for your new question... type this at the console
uname -a
and look for 386 or 686
that is your answer
to install the new kernel is not hard.
Just look in synaptic and search with 686 kernel, you should find it there.  then when you reboot, you will be in your newer kernel.btw, pick the newest version if you see more than one.8-[

---

### Post by jperez on 2006-07-03
Well, it seems that my system just doesn't like Linux as much as I do since I already have the i686 kernal installed.  Well, thanks for the help.  I guess this is just something I will have to live with. :-? 

Jesse~

---

