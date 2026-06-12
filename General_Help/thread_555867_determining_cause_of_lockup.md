---
title: "determining cause of lockup"
date: 2007-09-20
forum: General Help
---

### Post by gnychis on 2007-09-20
Hi all,

I am constantly getting a lockup problem on my x60s thinkpad.  I will be working, and bam the system is locked up.  I have to hard reset it using the power button and reboot.  How can I begin to determine what the cause of this is?

Thanks!
George

---

### Post by swisscow on 2007-09-20
Does it happen with a particular application? If you notice that it does try starting the application in a terminal and noting any error messages

---

### Post by gnychis on 2007-09-20
no specific application that i know of, I can let it sit idle at the desktop for a bit and it will lock up

---

### Post by HOLOGRAPHICpizza on 2007-09-20
I have a computer with this same problem, you can just let it sit and it will randomly lock up. i though there might be a problem with the ram, so I let memtest run overnight. It found no errors, and it can't actually fix anything, but for some bazaar reason it doesn't lock up anymore!:o

---

### Post by gnychis on 2007-09-25
this is becoming extremely annoying now... as it causes me to lose progress of work and such

I would greatly appreciate anyone who could suggest something

---

### Post by Uncle Che on 2007-10-18
I can't offer any advice but I am having the same issue.

---

### Post by gnychis on 2007-10-18
> **Uncle Che said:**
> I can't offer any advice but I am having the same issue.

I was able to solve my issue by determining it was my wireless.  It always seemed to freeze when my wireless lost signal and was trying to reconnect.  So, I checked out the newest SVN of madwifi and it solved it!

- George

---

### Post by rickggreen on 2007-10-18
In order to troubleshoot we need more info, start by at least giving us the hardware specs, CPU, video card/driver, memory. There is a lot of help here, Use search to scan the forums for the keyword "lockups' or "freeze". Also try IRC on the #ubuntu channel.

We have a lot of resources and friendly people here to help you.

---

### Post by WakkiTabakki on 2007-12-15
I'm experiencing similar problems on a Lenovo T61 with a Atheros 5418 wireless. I'm using madwifi from SVN, updating almost daily...
I've got no idea what the cause is, and have noticed no consistency as to when it freezes. The only common thing is when the system stops responding the Caps-Lock indicator starts blinking!

Have seen no freezes in Windows so far...


Cheers
/N

---

