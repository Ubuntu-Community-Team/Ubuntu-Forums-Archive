---
title: "Cannot use Su in terminal"
date: 2008-06-05
forum: General Help
---

### Post by erik33045 on 2008-06-05
when i am using terminal and i get asked to use the superuser password, i enter the right one, but it say it has an 'authentication failure'. But when i use all the other administrative tools like network and packet manager i enter the same password and it works. can someone help me out?

---

### Post by pedro_orange on 2008-06-05
System > Administration > Users and Groups.

Choose root, and give it a password not the same as any of the usr accounts.
If it's not that.....you could try resetting your keyboard settings? 

(I'm clutching at straws here)

Is this a fresh install by the way?

---

### Post by erik33045 on 2008-06-05
yes brand new

---

### Post by erik33045 on 2008-06-05
that did it, thank you!

---

### Post by perlluver on 2008-06-05
It's sudo apt-get install program instead of su>enter>password.

Edit:  Nevermind too slow...

---

### Post by richiewrt on 2008-06-05
Are you trying to "su root".  If so that won't work.  Use sudo to precede any command you need to run as root, or you can sudo -i to take root power for 15 min I think. root isn't set up with a password in Ubuntu as default.

---

