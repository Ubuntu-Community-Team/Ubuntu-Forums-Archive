---
title: "[SOLVED] install a package in an account that has no sudo permissions."
date: 2008-06-26
forum: General Help
---

### Post by adhg on 2008-06-26
Hi all,

I (sudo) created a new user and did not assign him sudo permissions; I would like to install some applications in his account (eg., java eclipse).

How can I do that from the command line?

when I type: sudo apt-get install fakeroot java-package

I get err 
NEW_USER is not in the sudoers file...

thank you

---

### Post by WRDN on 2008-06-26
Type "su" instead, and you will be prompted for the root password.
You can then install the packages as usual ("apt-get install [package]")

---

### Post by adhg on 2008-06-26
yep, thank you

---

### Post by bodhi.zazen on 2008-06-26
> **WRDN said:**
> Type "su" instead, and you will be prompted for the root password.
You can then install the packages as usual ("apt-get install [package]")

no, no, no :lolflag:

Add the new user to the admin group and have the new user user sudo.

No need to set a root password, just learn to user sudo.

[http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html)

---

### Post by adhg on 2008-06-26
but what if i don't wish him to have sudo rights?

---

### Post by bodhi.zazen on 2008-06-26
Well, that is the difference between su and sudo.

su = full access to root.

sudo = you can give more limited access to single commands or groups of commands.

If all you are needing is a root shell use sudo.

If you need to switch users either su to a user with admin rights.

Either way, no need to set a root password, which is my main point.

---

