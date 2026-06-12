---
title: "Gnome terminal broken (completely transparent) after update."
date: 2015-01-23
forum: General Help
---

### Post by chaywood on 2015-01-23
Hi,

I did a sudo apt-get update and then sudo apt-get upgrade and now my gnome-terminal is completely transparent. It still works (I can launch nautilus for example, or exit the terminal exits) however I can't see anything (see attachment).

I have searched the forums and havent found anything similar. I have tried reinstalling gnome term, resetting the config, and resetting compiz to no avail.

Has anyone experienced anything similiar?

OS: Ubuntu 14.04 LTS.

Cheers,
C

---

### Post by Erik1984 on 2015-01-23
Is it only the Gnome Terminal or other (GTK)-applications as well that are affected by this bug? I don't know much out Gnome but maybe you could try to reset the entire GTK-config, not just the terminal. And by resetting the config I mean removing (or renaming) the appropriate config directories from ~.

---

### Post by chaywood on 2015-01-23
Thanks for your suggestion Erik1984. I ended going a long winded journey of reinstalling GTK which fixed the issue.

---

