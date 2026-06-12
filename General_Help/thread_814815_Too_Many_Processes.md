---
title: "Too Many Processes"
date: 2008-06-01
forum: General Help
---

### Post by mlilien on 2008-06-01
I just started playing around with conky today and noticed that it's telling me that I have over 200 total processes.  I'd like to do some clean up, but I'm not sure where to begin.

What would be the best way to go about finding these processes, deciding which ones are unnecessary, and stopping them?

Thanks

---

### Post by ibuclaw on 2008-06-01
The simplest solution would be to go into the "**System>Administration>Services**" app and disable (uncheck) all services that you never use.
(ie: "**tracker**" or "**bluetooth manager**").

But for a more indepth overview, and a controlling of the lower system-level services (such as "**ssh**" and "**clamav**").

There is a nice how-to [right here.]("http://ubuntuforums.org/showthread.php?t=89491")

Regards
Iain

---

### Post by sdennie on 2008-06-01
tinivole is correct in how to reduce some of them but, you have to remember that 200 processes isn't actually that taxing on your system unless they are all trying to use the CPU or using lots of memory.  Unless your CPU usage, load average or memory usage is constantly high even when the machine is relatively idle, 200 processes isn't a cause for concern.  My machine shows 144 processes at the moment and a load average of 0.09 (close to idle) and memory usage about how I'd expect.

---

### Post by mlilien on 2008-06-01
Thanks.  I dropped about 30 processes with that howto.  I just want to make sure that I don't have anything unnecessary eating my batteries.

---

### Post by sdennie on 2008-06-01
If your primary concern is battery usage, dropping mostly idle processes isn't likely to help you much.  You'll want to look into the powertop tool and visit [www.lesswatts.org](www.lesswatts.org).  The last link in my signature provides a reasonable harness for taking all the interesting info you find from those two things and automating them.

---

### Post by ibuclaw on 2008-06-01
> **vor said:**
> If your primary concern is battery usage, dropping mostly idle processes isn't likely to help you much.  You'll want to look into the powertop tool and visit [www.lesswatts.org](www.lesswatts.org).  The last link in my signature provides a reasonable harness for taking all the interesting info you find from those two things and automating them.

+1
Useful stuff!

---

