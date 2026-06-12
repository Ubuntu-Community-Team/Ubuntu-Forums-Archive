---
title: "Windows ignoring LiveCD"
date: 2008-04-01
forum: General Help
---

### Post by Korarnithlas on 2008-04-01
First, to get any newbie stupidity of mine out of the way: My computer has 248 MB of RAM and the LiveCD requires 256 MB. It's hard to believe this could make a difference, but if it does, than, there you go, that's the problem. However....how do I solve it? It's all that is keeping me from installing Ubuntu. Hard to believe....

It's probably the above problem, but if not, than my computer is not recognizing the LiveCD for an unknown reason.

Either way, I need help, please.

---

### Post by ugm6hr on 2008-04-01
> **Korarnithlas said:**
> It's probably the above problem, but if not, than my computer is not recognizing the LiveCD for an unknown reason.

It may be the RAM - although the LiveCD should run (although installation may fail).  Do you have shared memory for graphics (that reduces system RAM).

What happens when you try and boot from LiveCD?

One solution - if you've decided to install Ubuntu - is to use the AlternateCD.

PS: Your title suggests you are trying to run the LiveCD from within Windows.  That is not how it works.  This might help explain [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by kellemes on 2008-04-01
I'd advice you to either use the Ubuntu alternate installdisk, install xubuntu (pretty cool), or one of the many other distro's out there..

Is it correct you cannot boot the livecd at all? If so..
Have you set your cd/dvd-drive to be first in the list of bootdevices in your BIOS?
This is needed to be able to boot from cd/dvd.

---

### Post by Korarnithlas on 2008-04-01
*Shakes head* Blast, I'm always unclear when I first post.

I can see the browser and "help to install Ubuntu" from the CD.

I can -not- boot from it.

*Ponders* I -may- have to switch to a different distro. It's a good idea to keep in mind (thx).

How would I do the BIOS thing?, which I've sort of read about in a book, but it didn't really explain it....

---

### Post by kellemes on 2008-04-01
Depends on your rig what key you need to get in BIOS.
In my case it's <DEL>
So.. start pc, and start tapping <DEL>

If not working just give us your specs and maybe someone can find out what spell you need to get it.

---

### Post by ugm6hr on 2008-04-01
F-keys are common to get into BIOS. Often F10 or F12.

---

### Post by forrestcupp on 2008-04-01
Usually when you start your computer and the start up words come on your screen at the very beginning it will tell you what key to press to get into your bios settings.  Like the others said, it's usually either DEL or one of the F keys.  When you get into that, you'll have to navigate around the settings and find the boot options.  Set the 1st boot source to be CD and the 2nd one to be your hard drive.

---

### Post by Korarnithlas on 2008-04-01
HAH!

I've gotten it to work. Granted, my computer decided to not let me view anything through the Start/Install choice, which I think is maybe due to the low RAM, but thankfully, it's working.

Thank you everyone for your help. For some future reference, I also watched a few videos of LabRats (talking about getting into BIOS, etc.).

Here is a question though: It may take 257 RAM to view the Live example and play around.....but does it need that much to install and use? Obviously, more RAM is better, and I definitely plan to get more, but for an initial install and tweaking and use of?

---

### Post by forrestcupp on 2008-04-01
You probably should try Xubuntu.  It takes less resources.

---

### Post by Korarnithlas on 2008-04-01
*Sighs* Agreed.

---

### Post by ugm6hr on 2008-04-01
> **Korarnithlas said:**
> *Sighs* Agreed.

Remember that once installed, Ubuntu will be faster than with the LiveCD.

However, you may run into problems installing unless you use the AlternateCD (since this uses less RAM than the LiveCD install).

But Xubuntu is not a bad option (I started with it on Feisty), and actually has some nice options missing in Gnome (normal Ubuntu).

---

### Post by Korarnithlas on 2008-04-03
Thank you all.

I'll try Xubuntu instead.

By the way, if I'm going to be burning the ISO file onto a CD, is there a -type- of CD that is better for such things?

---

### Post by ugm6hr on 2008-04-03
> **Korarnithlas said:**
> By the way, if I'm going to be burning the ISO file onto a CD, is there a -type- of CD that is better for such things?

CD-R rather than CD-RW (although the latter generally works OK).

I think that Ubuntu fits on 72 and 80 min CDs, but not 100% sure.

---

