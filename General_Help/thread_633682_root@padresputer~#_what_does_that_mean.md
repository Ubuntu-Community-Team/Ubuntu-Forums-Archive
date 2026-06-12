---
title: "root@padresputer:~# what does that mean?"
date: 2007-12-06
forum: General Help
---

### Post by famous3warriors on 2007-12-06
Pleas help I did a fresh install of ubuntu studio 7.10 and i could never get into the log in screen so I did a recovery reboot and I get this root@padresputer:~# root.  What do I have to do to get my puter working or what did I do wrong and how can I fix it.

---

### Post by g2g591 on 2007-12-06
try running this command (by typing it in then pressing enter at that root promt (root is the automaticly created user that has the power to edit any file anywhere on your system regardless of owner, the # means your at a console logged on as root where you can enter commands (and hopefully save your system)) dpkg --configure -a, then apt-get install -f , then run apt-get install ubuntustudio-desktop . your install seems to be messed up, but running these commands should install every thing to get it back right. If you get a command not found, first check for typos, then if it doesn't work reinstall (run the verify cd option first though)

---

### Post by famous3warriors on 2007-12-06
thank you for your help I really do appreciate this I will do that thank you once again.

---

### Post by g2g591 on 2007-12-06
did it work? dpkg --configure -a is the thing to run if an install might have been inturupted, apt-get install -f fixes any dependancy issuses and because you're running ubuntu  studio, apt-get install ubuntustudio-desktop installs all the stuff that would normally have been installed with ubuntu studio. Oh and if you might need to run these commands from regular terminal, prefix them with sudo to run them as root (your normal user doesn't have permission to do those things)

---

### Post by famous3warriors on 2007-12-06
no i keep getting the same old thing I tried even reinstalling and it is not working I guess I have to go back to ubuntu 7.10 i386 i really like the ubuntu studio and what it had to offer.

---

