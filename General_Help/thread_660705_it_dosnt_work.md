---
title: "it dosnt work"
date: 2008-01-07
forum: General Help
---

### Post by evilhamburger on 2008-01-07
ok, I own an Acer Laptop with Vista on it.

I tried installing ubuntu, but when I resart to start instellation, it comes up with ubuntu OR vista, I click ubuntu and then it comes up with a loading thing before changing to a command promt. The command propt is impossible to get out of and I have to restart rthen go windows again

can some1 tell me why? or how to install it?

BTW, I downloaded the 700Mb CD and installed it by clicking wubi-cdboot

---

### Post by Sef on 2008-01-07
Moved to Wubi forum.

---

### Post by ago on 2008-01-07
> **evilhamburger said:**
> ok, I own an Acer Laptop with Vista on it.

I tried installing ubuntu, but when I resart to start instellation, it comes up with ubuntu OR vista, I click ubuntu and then it comes up with a loading thing before changing to a command promt. The command propt is impossible to get out of and I have to restart rthen go windows again

can some1 tell me why? or how to install it?

BTW, I downloaded the 700Mb CD and installed it by clicking wubi-cdboot

If you use wubi-cdboot you need to have the CD inserted before you reboot

---

### Post by evilhamburger on 2008-01-08
I had the disk in, it comes up with the boot options and I pick linux. 

then it starts the thing with the little red bar running across the screen (presumably the loading screen)

after a bit it comes up with a command prompt, why?

---

### Post by evilhamburger on 2008-01-08
and can this go back to the installing forum?

---

### Post by ago on 2008-01-09
If you boot wubi, hit esc when you get a countdown, then select verbose mode

At the shell you can now look at the logs in /tmp and /var/log
You can use the "cat" and "more" commands to read the logfiles

---

### Post by mikedep333 on 2008-01-10
It might be helpful to post what laptop you have. Sometimes brand new systems will not work easily or at all. You should google: ubuntu "acer laptop model" - and see if anyone has it working.

---

