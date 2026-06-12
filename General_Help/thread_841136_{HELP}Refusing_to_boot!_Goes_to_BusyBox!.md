---
title: "{HELP}Refusing to boot! Goes to BusyBox!"
date: 2008-06-26
forum: General Help
---

### Post by !@!@! on 2008-06-26
Okay,
heres what happened.
My stupid friend hit the off button on my power supply while Ubuntu was up and running.
I'm using Wubi and WinXP boots fine, but Ubuntu goes to the loading screen the little bar almost makes it to the other side, then it cuts to Busybox.
I tried to type "exit" in, but it doesn't do anything.
I cannot figure out what to do.
Can someone point me in the right direction?

Some notes:
-I'm using 8.04 Home
-My hard drive is fine
-I'm a linux n00b. :P

---

### Post by !@!@! on 2008-06-26
Bump! This Is Urgent Please!

---

### Post by knutschr on 2008-06-26
The kernel you try to use is corrupted, I think.
Start with another and reinstall it.

---

### Post by !@!@! on 2008-06-26
> **knutschr said:**
> The kernel you try to use is corrupted, I think.
Start with another and reinstall it.
thanks, but it does nothing. i tried.
some more info;;
I tried replacing the root=UUID=xxxx with root=/dev/sda3 on GRUB
it made it just not start, and it didnt cut to busybox.
the problem is there.

---

