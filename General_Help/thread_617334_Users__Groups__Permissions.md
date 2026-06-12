---
title: "Users / Groups / Permissions"
date: 2007-11-19
forum: General Help
---

### Post by henkasdf on 2007-11-19
Hi all,

How do I make a certain user part of the root group while using the terminal (command line)

Your help would be much appreciated!!

Thanks

---

### Post by jumping_snake on 2008-02-18
A question to you: do you have to be in the root group or do you just require "root" abilities? If you could add yourself to the sudoers file (/etc/sudoers), you'll be able to enter the command "sudo" followed by your password and then you'll have root access to the system.

Does this help?

---

