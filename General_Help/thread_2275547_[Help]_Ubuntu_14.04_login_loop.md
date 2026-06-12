---
title: "[Help] Ubuntu 14.04 login loop"
date: 2015-04-27
forum: General Help
---

### Post by danny47 on 2015-04-27
My system had completely frozen so i had to hit the power button. I booted back up but when i enter my pass for main account it goes to black screen, does ubuntu notification sound and goes back to login screen. Guest account does the same. I am writing on my android atm so spelling nd grammar will be terrible. Really new to ubuntu btw. Running Ubuntu 14.04 LTS x64

---

### Post by dino99 on 2015-04-27
you should try the 'recovery mode' when grub menu appear  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
and after having activated the network into the submenu, select to fix the system.
opening the terminal (console) let you update/upgrade if necessary

---

### Post by sebastiaan5 on 2015-04-27
try ctrl+alt +f1   (ctrl alt f7 to end)

and do the command:

```
sudo mv .Xauthority .XauthorityBak
```

this helped me when my login screen looped.


greetz

---

