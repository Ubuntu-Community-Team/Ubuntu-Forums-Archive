---
title: "Login"
date: 2005-09-22
forum: General Help
---

### Post by Christopher999999 on 2005-09-22
I have installed Ubuntu but I did not set up a user. I gave it a master password. How do I get in the master account :-?

---

### Post by Christopher999999 on 2005-09-22
If I type in root, and then te password, I get a message that I cannot login from this screen as the system administrator. HELP!!!!!

---

### Post by frodon on 2005-09-23
Ubuntu do not create a root account, if you want to run root commands, use sudo before the command to run and you will run it as root.
If you want to become root in a terminal type  : ```
sudo su
```Endeed the root password is the same as your user password, you can change that if you want, up to you.

---

### Post by fordfan753 on 2005-09-23
[QUOTE=Christopher999999]If I type in root, and then te password, I get a message that I cannot login from this screen as the system administrator. HELP!!!!![/QUOTE]

If you've really screwed up you can log into failsafe from grub (tap escape before ubuntu boots) and create a user account, then log back into normal ubuntu and use the account to log into GDM normally.

---

