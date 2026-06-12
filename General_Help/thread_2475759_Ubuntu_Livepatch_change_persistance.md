---
title: "Ubuntu Livepatch change persistance"
date: 2022-06-07
forum: General Help
---

### Post by ye-yang98 on 2022-06-07
Hi there, I have a question regarding the Ubuntu Livepatching process.

Say for instance we have to reboot an Ubuntu Server with Livepatch enabled, **unrelated **to a kernel upgrade, do the changes introduced by the Livepatch service persist after the server boots up or are they reapplied once the Livepatch service is up and running?

---

### Post by #&amp;thj^% on 2022-06-07
Applied at boot as well.
Livepatch eliminates the need for unplanned maintenance windows for high and critical severity kernel vulnerabilities by patching the Linux kernel while the system runs. Reduce fire drills while keeping uninterrupted service with the Ubuntu Livepatch service.

---

### Post by ye-yang98 on 2022-06-07
So would it be correct to assume that there is a brief period in which the Kernel is unpatched right after the server boots up? This would mean that the changes are made on the fly by the Livepatch service rather then being directly modified in the Kernel, please correct me if I'm wrong.

---

### Post by #&amp;thj^% on 2022-06-07
Its being over thought here, more info on the subject: [https://ruffell.nz/programming/writeups/2020/04/20/everything-you-wanted-to-know-about-kernel-livepatch-in-ubuntu.html](https://ruffell.nz/programming/writeups/2020/04/20/everything-you-wanted-to-know-about-kernel-livepatch-in-ubuntu.html)

---

### Post by deadflowr on 2022-06-07
Are you not running regular updates or something?
A regular update will have installed a new kernel which will have the patches already built into it.
Making whether or not livepatches persist moot.

---

### Post by #&amp;thj^% on 2022-06-07
> **deadflowr said:**
> 
Making whether or not livepatches persist moot.

And enough sed>>>(said)

---

### Post by grahammechanical on 2022-06-07
Speaking in my ignorance ... 

> Say for instance we have to reboot an Ubuntu Server

Surely, that would be the time to run update/upgrade and get the latest kernel. And then there is this statement from the link provided by @1fallen:

> Livepatch is more of a temporary band-aid  solution, reserved for fixing critical security issues until such a time comes when the host can be rebooted into a updated kernel.

Regards

---

### Post by #&amp;thj^% on 2022-06-07
@grahammechanical I'm going to pirate your statement, seems to get to the point nicely. Well worded!

---

### Post by ye-yang98 on 2022-06-07
Thanks for the link, I'll read up on it.

---

