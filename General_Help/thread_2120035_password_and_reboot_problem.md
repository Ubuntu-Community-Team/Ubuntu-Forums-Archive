---
title: "password and reboot problem"
date: 2013-02-25
forum: General Help
---

### Post by hollypk on 2013-02-25
I'm a new Ubuntu user (as of two days ago) and am having a problem with my admin password. I got an asus x201e preloaded with ubuntu. It came with a temporary admin user, and I added an admin user. I was not prompted to create a password for this user, but am asked for the password each time I try to do an admin task (in the users panel under system settings it says "account disabled" in the password box).  Now under the original temp user I don't have admin privileges, and therefore can't make any changes to the system. Everything I have tried requires me to have the admin password, which to my knowledge doesn't exist! I've tried potential default passwords (carriage return, admin, password, default, ubuntu) but none of them has worked.

I have tried to reboot in rescue mode as recommended by a few posts I read, but the system does not actually seem to reboot. The screen goes blank when I restart or shut down, then very shortly returns to ubuntu. Holding down the shift key during this process doesn't change anything. I'd like to try this as my next step, but am not sure how to get a proper reboot to the grub menu.

Hope someone can help! thanks. Otherwise I really like using Ubuntu, and am eager to continue.

holly

---

### Post by matt_symes on 2013-02-25
Hi

Welcome to the forums :popcorn:

Lets get some information first

Open a terminal and type

```
groups
```

Copy and paste the output into your next post.

Do the same for this command

```
cat /etc/default/grub
```

Kind regards

---

### Post by fdrake on 2013-02-27
to create or change a user's password follow this link in my blog:
[http://theguyonthe3rdfloor.wordpress.com/2013/02/27/ubuntu-lost-password/](http://theguyonthe3rdfloor.wordpress.com/2013/02/27/ubuntu-lost-password/)

---

