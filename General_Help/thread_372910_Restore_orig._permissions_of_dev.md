---
title: "Restore orig. permissions of /dev ?"
date: 2007-02-28
forum: General Help
---

### Post by ^rooker on 2007-02-28
Unfortunately, a small typo in the shell made me change the permissions of /dev/* ... 

Is there any way to restore their original permissions?

---

### Post by ofek on 2007-02-28
First thing we need to know is what was ur typo. The reason for that is because u might have changed all premissions of the files inside /dev (recrusive) or only changed the dir's permission. In anyway ur solution lays in the hands of our dear friend the "chmod" command.

---

### Post by llamakc on 2007-02-28
Did you do this in the terminal? BASH has a history and you can find out precisely what you did.

---

### Post by po0f on 2007-03-01
^rooker,

Does a reboot not fix them?

---

### Post by ^rooker on 2007-03-16
After reading myself a bit into udev, I figured out that a reboot might fix things (since udev creates /dev at startup, based on rules, anyway)

I was just scared to reboot and find my PC in a completely useless/locked out state - but everything's fine and back to normal now. 

thanks!

---

