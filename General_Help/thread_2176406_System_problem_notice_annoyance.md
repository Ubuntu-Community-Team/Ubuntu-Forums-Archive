---
title: "System problem notice annoyance"
date: 2013-09-24
forum: General Help
---

### Post by Lloydb39 on 2013-09-24
Periodically, a window pops up notifying me of a "system error" and asking if I want to report the problem. It never tells me what the problem is or how I can fix it. I don't notice any problem. Everything seems to work as expected. Does anyone know how I can find and fix whatever is producing the error message? I have 12.04 64-bit on a homemade AMD machine.

---

### Post by slickymaster on 2013-09-24
System crash detected reports can be very annoying, especially when nothing seems to be going wrong. The culprit is Apport, a software error/crash reporting tool for Ubuntu, which is supposed to be in disabled state for stable releases.
It is very simple to disable it just edit the file **/etc/default/apport**, and change the enabled setting from enable=1 to **enable=0** then save.

---

### Post by Lloydb39 on 2013-09-24
Before I do that, it isn't a system "crash." Nothing happens. The exact notice is: "System program problem detected." So, should I proceed?

---

### Post by slickymaster on 2013-09-24
> **Lloydb39 said:**
> Before I do that, it isn't a system "crash." Nothing happens. The exact notice is: "System program problem detected." So, should I proceed?

Sorry, I didn't correctly interpreted the meaning of your original post.

Is this the message that pops-up? [ATTACH=CONFIG]246471[/ATTACH]

If it is just open a terminal window and run the following:```
sudo rm /var/crash/*
```This will remove any old crashes, that might still be reported (in error). After a reboot/re-starting, any further pop-ups still need to be investigated.

---

### Post by Lloydb39 on 2013-09-26
I think that did the trick. Thanks.

---

