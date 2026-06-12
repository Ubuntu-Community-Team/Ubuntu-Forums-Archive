---
title: "How to locate instability issues?"
date: 2007-06-01
forum: General Help
---

### Post by clicks on 2007-06-01
I ran Feisty installations on two different systems, while the first one runs very stable on my Samsung X60 Notebook, the second one is quite unstable and locks up 2 - 3 times a day! The system crashes mostly during phases where the processor is more or less idle. The whole system simple freezes, no chance to change to another shell or similar.
How can I try to find out which part of my setup is causing these issues? As the system hangs-up immediately it isn't able to write anything into the syslog or similar.  Are there any other sources or tools I can use to find details about my problems?

---

### Post by gerscht on 2007-06-01
I had similar issues (low CPU usage but high disk activity) and I narrowed it down to Beryl/Emerald.
Do you have them installed?
Since I've disabled them, it hasn't frozen once (touch wood ;)

---

### Post by faceoftheearth on 2007-06-01
I don't know if it's been fixed, but back in the day I had the same problem with Ubuntu and it turned out that it was polling the DVD drive and when it found nothing it would just freeze up. See if it still freezes when you have something in the drive.

---

### Post by EndPerform on 2007-06-01
Also, if you have SSH installed on the machine that's locking up, try to SSH into it when it locks.  If you can get in, you'll be able to troubleshoot a bit better.  For instance, my desktop has been locking, and I could still get into it... turns out I have an issue with Xorg :)

---

### Post by clicks on 2007-06-01
Thanks for your ideas, will try all that. Also the DVD issue sounds quite weird (and I have three DVD drives).
Yes I have Beryl running, it was one of mine first suspects. A switch to Compiz didn't solve the problem, I will try to test it some days without those woobly windows.

---

