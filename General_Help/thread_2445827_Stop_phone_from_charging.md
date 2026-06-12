---
title: "Stop phone from charging"
date: 2020-06-20
forum: General Help
---

### Post by MibunoOokami on 2020-06-20
Hi all,
 
 
 A pretty straightforward question. Is it possible to stop a USB port from charging a tethered cellphone in Ubuntu 18.04?
 
 
 Thanks in advance.

---

### Post by CelticWarrior on 2020-06-20
I think a pretty straightforward answer is in order: No, it isn't.
One of two things must happen for the phone not to charge when connected: 1. Stopping the USB port from outputting 5V current - can't be done as that is part of the USB standard - or 2. making the phone not to accept charge when connected - can't be done without major reprogramming that would very likely break the phone forever.

---

### Post by lvm on 2020-06-20
> **CelticWarrior said:**
> making the phone not to accept charge when connected - can't be done without major reprogramming that would very likely break the phone forever.
This is not entirely true, rooted android can do this e.g. using blex (magisk module). No root - no luck.

---

### Post by MibunoOokami on 2020-06-21
Thanks for your replies. 

I found a solution today and that&#8217;s to use the mobile hotspot feature on my phone... Don&#8217;t know why I didn&#8217;t think about it sooner, or why I didn&#8217;t add in my original post the tethering was for the internet.

---

### Post by CelticWarrior on 2020-06-21
**An important note for future readers: The thread is marked [solved] by the OP but the OP didn't find nor implemented any solution to the problem in question.**

The OP found out an workaround - WiFi tethering - that avoids the USB connection with the phone. Such solution couldn't be used if the computer hasn't a working WiFi.

---

