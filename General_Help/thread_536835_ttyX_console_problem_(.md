---
title: "ttyX console problem :("
date: 2007-08-28
forum: General Help
---

### Post by AranelSurion on 2007-08-28
I installed new kernel, and It works wonderful, but In my new kernel, when I use CTRL + ALT + F1 , F2 .. , It only gives black screen. How can I get back ttyX consoles ? This is very problematic for me :/

Thanks,

---

### Post by K.Mandla on 2007-08-28
Inside /etc/event.d/ are there tty1, tty2, tty3, etc. files?

---

### Post by AranelSurion on 2007-10-19
@K. Mandla

Yes, there are.


Edit: I upgraded my Feisty Fawn to Gutsy Gibbon, and my ttyX consoles doesn't gives black screen anymore, but It only gives a flashing "_" and  I still can't use them.



P.S: Yes, I'm not good at English language :)

---

### Post by caldevil on 2007-10-19
Its a documented problem:
[https://bugs.launchpad.net/bugs/129910](https://bugs.launchpad.net/bugs/129910)

You can not use framebuffer with gutsy right now. A temporary fix is to remove `vga=` line from the kernel boot parameter (see the bug for details)

---

### Post by AranelSurion on 2007-10-21
> **caldevil said:**
> Its a documented problem:
[https://bugs.launchpad.net/bugs/129910](https://bugs.launchpad.net/bugs/129910)

You can not use framebuffer with gutsy right now. A temporary fix is to remove `vga=` line from the kernel boot parameter (see the bug for details)

I removed "vga=" line  in menu.lst and rebooted my system, tty[1-6] works but it is very problematic. Example ; When I give a command, i can't see my command! After 5x ENTER , i can see it and my systems answer. It's very annoying.

---

