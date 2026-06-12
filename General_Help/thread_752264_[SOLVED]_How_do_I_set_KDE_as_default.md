---
title: "[SOLVED] How do I set KDE as default?"
date: 2008-04-11
forum: General Help
---

### Post by Growbag on 2008-04-11
Before I start, I DO NOT USE GDM/KDM, so that is not the solution :).

This is a server install (7.10) where X is started from the command line.

I'm sure it is a simple *dpkg-reconfigure* command, but on which package?

Thanks in advance for any help.

---

### Post by ibutho on 2008-04-11
Edit or create a file called ~/.xinitrc and enter the commands "exec startkde" (minus the quotes). That will make sure that KDE is started whenever you run "startx".

---

### Post by Growbag on 2008-04-12
Excellent, works a treat :)

Thanks ibutho.

---

