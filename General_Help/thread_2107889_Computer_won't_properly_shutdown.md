---
title: "Computer won't properly shutdown"
date: 2013-01-23
forum: General Help
---

### Post by fakedave on 2013-01-23
Hello,

I have installed Ubuntu 12.10 then KDE on top. I very much like it and started using it for work.
At the same time I still try to setup 4 screens and played with $£*@@#$ drivers for my HD 6450.
After messing around a bit it turns out that my computer won't shutdown anymore when using the desktop shortcuts.
I go to the console and 'sudo shutdown now' and even with that the computer hangs on the shutdown screen.
When I log back in, my desktop settings have not been saved and Chrome is not happy.

How can I know what's holding the process?

Thanx a lot.

---

### Post by dino99 on 2013-01-23
set the verbose mode on to let you see the shutdown comments:

remove "quiet splash" from /etc/default/grub, then update-grub again

---

### Post by fakedave on 2013-01-23
Thanx for that.
I did what you said but the thing is that even if I send the reboot from the console, it switches to the graphical interface to the logout screen from ubuntu (the one with the dots).
Therefore I don't see anything of the problem ...

Is there any file somewhere that contains the log?

---

### Post by e8hffff on 2013-02-08
> **fakedave said:**
> Thanx for that.
I did what you said but the thing is that even if I send the reboot from the console, it switches to the graphical interface to the logout screen from ubuntu (the one with the dots).
Therefore I don't see anything of the problem ...

Is there any file somewhere that contains the log?

Got the same problem.

---

