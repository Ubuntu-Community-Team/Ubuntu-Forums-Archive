---
title: "different user and sudo passwords"
date: 2008-06-16
forum: General Help
---

### Post by covert215 on 2008-06-16
I understand that the default root/sudo password is the same as the password of the first user on the system.  How can I set it so that the two passwords are different?

---

### Post by pdwerryhouse on 2008-06-16
You can't. Sudo is designed to use the password of the user that is calling it.

What you can do is to give your box a real root password; ie, a password for the root account. To do this:

sudo su
passwd root

It will ask for a new password (twice). Once you've done that, you'll be able to either log into the server as root, or su to the root user, with the new password. Eg:

su -

---

### Post by aysiu on 2008-06-16
If [this](http://ubuntuforums.org/showthread.php?p=1053358#post1053358) doesn't help you, I doubt anything will.

Why do you need a separate password?

---

