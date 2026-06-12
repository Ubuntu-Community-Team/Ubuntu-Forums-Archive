---
title: "Printing"
date: 2007-08-13
forum: General Help
---

### Post by i486dx266 on 2007-08-13
I try to add a printer as a desktop user, and i'm asked for the administrator pwd - i assume root, but when i enter the pwd for root it says wrong pwd. What gives?

---

### Post by xc3RnbFO8P on 2007-08-13
Have you tried to restart your computer, I got this problem sometimes with wireless keyboard.

---

### Post by 1/0 on 2007-08-13
Its the same as your user pw. Root accounts are disabled per default in *buntu. Give that a try instead.

---

### Post by i486dx266 on 2007-08-13
tried rebooting and tried all pwds, root, an administrator user, and the desktop user pwd. :confused:

---

### Post by xc3RnbFO8P on 2007-08-13
Read this: [http://ubuntuforums.org/showthread.php?t=273531&highlight=lost+password]("http://ubuntuforums.org/showthread.php?t=273531&highlight=lost+password")

---

### Post by i486dx266 on 2007-08-13
Changing the pwds is no problem, i've already done that from another user account with administrative rights. The problem seems to be with the sudo command. As a regular user (no check for administer system under system - administration - users and groups) i am asked to su root as i click add printer, but alas neither the root pwd, the pwd of a user with administrative rights, or the current user (user1) works. Now if i logout - login as an administrator - change user1's rights to administrator and log in again as user1 - then i can add a printer... But it should have worked with sudo...](*,)

---

### Post by xc3RnbFO8P on 2007-08-13
It seems that you have to reinstall.

---

