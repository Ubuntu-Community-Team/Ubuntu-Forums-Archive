---
title: "Shutting down ubuntu"
date: 2008-07-04
forum: General Help
---

### Post by JustGus on 2008-07-04
I can't get Ubuntu to shut down properly.  I posted details of it [earlier]("http://ubuntuforums.org/showthread.php?p=5304712#post5304712"). In the absence of a solution to the problem I'd  like to know whether simply pulling the plug is likely to do harm to the system.  Any advice on this would be very much appreciated.

Cheers,

Gus

---

### Post by prshah on 2008-07-04
> **JustGus said:**
> 
In the absence of a solution to the problem I'd  like to know whether simply pulling the plug is likely to do harm to the system.  


Theoretically, it should do not harm; ext3's journaling file system feature sees to that.

Practically, however, if you happen to yank out the power just when the HDD is about to go active there is a good change you will end up bad sectors.

However, you can try this: Having read your other thread:```
sudo halt -i -p
``` That should bring your system down gracefully, and (most likely) turn it off. If it doesn't turn it off, you can then turn off the power when you get the message "System Halted".

Post back if you have questions...

---

### Post by JustGus on 2008-07-04
Thanks that's a great help...I think I may already have trashed it though - turned on my machine but inexplicably the monitor isn't getting any input signal.  Fiddled with all the cables, rebooted, fiddled some more rebooted some more and nothing.  A black screen.  Could this have been due to turning it off from the plug?  
I also tried rebooting from the original CD, thinking that somehow the OS or BIOS may be telling it to stop the signal, but can't get it to boot off anything other than the HDD.
If anyone out there can suggest anything to get my monitor going I'm all ears!
I'm running Hardy on a MiniITX machine.
:(
Gus

---

