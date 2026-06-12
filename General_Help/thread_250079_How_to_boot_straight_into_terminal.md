---
title: "How to boot straight into terminal?"
date: 2006-09-03
forum: General Help
---

### Post by jamesrose on 2006-09-03
I need to exit X, too install my (Nvidia) graphics card drivers, how do i boot straight into a terminal with no GUI?


Thanks!

---

### Post by Ramses de Norre on 2006-09-03
Just for once? Press ctrl+alt+F1 after a normal boot to get a tty (text only) do the installation and then ```
sudo /etc/init.d/gdm restart
``` to restart gdm (replace by kdm when needed).

When you're not able to boot normally you can try the recovery mode which will drop you at a root shell.

---

### Post by jamesrose on 2006-09-03
lol or just presst Ctrl alt and F7 again, Thanks alot mate!

---

### Post by Ramses de Norre on 2006-09-03
I saw I told to use F7 for tty but it's everything from F1 to F6 =)
But it seems you understand what I meant anyway ;)

---

### Post by Anduu on 2006-09-03
You are better off to boot into recovery mode from grub because doing a ctrl+alt+F7 still leaves gdm running and there is the possibility that trying to install new drivers may not work because the old ones are still in memory/use...

---

### Post by Ramses de Norre on 2006-09-03
That's why he has to restart gdm.

---

### Post by jamesrose on 2006-09-04
Everything worked correctly, Thanks.

I used Ctrl+Alt+F1 to get in to the terminal and Ctrl+alt+f7 to get out :-D

---

