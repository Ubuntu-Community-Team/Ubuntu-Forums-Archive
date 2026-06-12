---
title: "Weird restarting and freezing symptom in Ubuntu 7.04"
date: 2007-05-31
forum: General Help
---

### Post by xanvier on 2007-05-31
Greetings everyone,

very new to Linux scene and recently on my copy of Xubuntu 7.04, i frequently encounter lotsa freezing. The HD indicator on my PC casing would flash rigorously for a while and very soon after, i will be brought back to the login page automatically.

After that, i would have to type in my username and password again.

When i'm in the desktop, i would also frequently encounter application freezing up. I would proceed to the "Process Manager" and terminate or kill the application.

All these did not happen until recently. Would love to hear your advise! Thank you very much!

---

### Post by xanvier on 2007-06-03
Upz.

---

### Post by xanvier on 2007-06-10
I suspected this issue to be a memory related one. Therefore i used memtest86+ v1.65 available in the grub menu to test out the rams.

When test #5 ended, i was presented with a list of "failed address". It more or less confirmed the notion that the memory is faulty. 

However, something still bothers me. Is the failing addresses presented in test #5 the main reason for crashes and hangs? Is it normal for rams to have some failing addresses?

Thank you!  Really love to hear from any one who have knowledge on this area.

---

### Post by xanvier on 2007-06-11
Upz...

---

### Post by GraveyardPC on 2007-06-11
Your memory should never fail any of those tests. If you have multiple sticks, try to deduct which one is throwing errors and load the OS with the working one(s). Then you'll really know if that was the main issue.

---

### Post by bishop9226 on 2007-06-11
yeah you can do what the guy above me said.  but usually any and all hangs frequent hangs are due to - bad memory, bad psu, bad mobo, bad chip.  memory is first and easiest thing to test.  if that is failing then you know what the problem is.  find the stick and remove it, see how it runs before going out and buying a new one id say.  make sure to memtest again til you get 0 errors

---

