---
title: "Manual FSCK"
date: 2008-02-04
forum: General Help
---

### Post by Emceay on 2008-02-04
Ubuntu (Gusty) fails to run a disc check at boot.
Then it starts maintenance mode and tells me to run fsck manually..
I've done this a thousand times now and every time I ctrl+D or type 'exit' the system restarts and hangs on the disc check - forcing me to run it manually again. I'm sick of this loop. What am I supposed to do to get back into Ubuntu again? :-x

---

### Post by goodfella on 2008-02-04
Can you please post the error message you are getting when sent to a maintenance console?  I have had some recent problems with fsck my self so I may be able to help you but I need more information, thanks.

---

### Post by Cannaregio on 2008-02-04
This COULD (underlined: *could*) work:
from live-cd, use gparted  in order to check if your main hard disk is sda1 or whatever 
and then ([COLOR="Blue"]sda1[/COLOR] ONLY if your disk is sda1, check in gparted)

```
e2fsck -b 32768 /dev/[COLOR="Blue"]sda1[/COLOR]
```

good luck.

---

### Post by Emceay on 2008-02-04
> /dev/hdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
fsck died with exit status 4


This whole thing started when I got a really non-descriptive warning message on logout/shutdown that said something was wrong with X, and to talk to a system administrator - and the display would be disabled. Since the keys did nothing at this point, I restarted; and lo and behold it says that fsck failed.

I ran the e2fsck -b 32768 command on the drive in question. And it pretty much did the same thing, at the end, I type exit (or ctrl+d) and the system says it failed to start the maintenance shell and restarts.. On the restart i get the ubuntu logo with the bar, then halfway through it drops out to text and starts trying to check the file system... which is of course broken, and sends me back to the maintenance shell to trying the whole process again.

At this point I'm pretty sure whatever was on my harddrive is destroyed, but I'm crossing my fingers that I can get back in. This situation seems to happen to me no matter what version of Ubuntu I use.. Anyone that says you don't need to know command line is a bold-faced liar.

---

### Post by Emceay on 2008-02-04
Is there a way to tell the maintenance shell to reboot without running a disc check? It seems to always check once I'm finished running fsck.

---

### Post by longhornxtreme on 2008-03-03
Have you tried a "fsck -y /dev/XXXXX"

?

---

