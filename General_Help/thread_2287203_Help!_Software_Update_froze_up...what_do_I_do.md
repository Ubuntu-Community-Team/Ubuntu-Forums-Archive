---
title: "Help! Software Update froze up...what do I do?"
date: 2015-07-17
forum: General Help
---

### Post by egruber on 2015-07-17
I'm running about a 175 mb update today on my Ubuntu installation.  It got as far as 'setting up cups-bsd (2.0.2-lubuntu3.2) and it has been stuck there for awhile.  My hard drive just spins and nothing happens.  What do I do without crashing the PC and ruining the OS?  Thanks!

---

### Post by oldfred on 2015-07-17
Remember the elephants.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

And if you can get to terminal run top to see what is running by pid & kill that task only.
       top
# use q to quit top
 sudo kill pid

---

### Post by egruber on 2015-07-17
Thanks you SO MUCH for that tip!  I never heard of it and it worked.  Now that I'm back up, do I rerun the software updater to pick up the remainder?

---

### Post by oldfred on 2015-07-17
The question then is what caused it to stop.

Sometimes the mirror you are using is in the middle of updating, but then you usually get a partial update message.
Do you have any ppa's enabled that may now have issues?

Or have you not run fsck on your ext4 partition(s) lately or you have hardware type issues.

---

### Post by egruber on 2015-07-17
I apologize for the ignorance and I don't wish to appear ungrateful, but your questions are well beyond my knowledge of Unix.  All I can say is that I have used Ubuntu on this PC for years and never had any issues applying software updates.  Once the PC locked up and I restarted it, I re-ran the Software Updater and it surprisingly picked up where it left off.  Once completed, it prompted for a reboot and all has been fine since.  I hope this is a one-off incident.

---

