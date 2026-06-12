---
title: "[SOLVED] root account"
date: 2007-09-08
forum: General Help
---

### Post by deets52 on 2007-09-08
OK, I am new again to Linux. It has been years since I played around with it. A lot has changed (and I have forgotten even more!). When I installed the desktop and server it never asked me for the root password. I know *that is not needed anymore* but I don't understand it totally. I have been using the sudo command and it work pretty good, but I have some questions.

First, What is default password for the root account? Is it a generated password that's different on each system?

Second, Can I change it or will it cause problems? Even if I can't use it I still would think about this.

Third, Is it even possible to use the account? 

Thanks in advance.

---

### Post by apetresc on 2007-09-08
> **deets52 said:**
> First, What is default password for the root account? Is it a generated password that's different on each system?
There is no root account, per se. Every user who you want to be able to do root-like things get added to the 'admin' group. Then THEIR individual password becomes like a root password, in the sense that 'sudo' will work for them. There is no one, single root password.

> **deets52 said:**
> Second, Can I change it or will it cause problems? Even if I can't use it I still would think about this.
You can change it as simply as changing your own user's password. Just type "passwd" at a terminal.

> **deets52 said:**
> Third, Is it even possible to use the account? You *can*, but it is highly not recommended. Ubuntu's way of doing it is really quite elegant once you get used to it :)

---

### Post by aysiu on 2007-09-08
Read this link:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It will answer all your questions. Seriously.

---

### Post by deets52 on 2007-09-08
Thanks for the quick reply. There is so much to learn.

I understand the sudo and the admin group, but not the root account. One thing I always liked about Linux is the method of security over Windows (lack there of in their case). I don't want to use the root account, I was just wanting to see if it should or could be changed. If there is a default password on all machines, I don't want that. I also don't want to just give out admin access to everyone. So that leads me to more questions.

How can I limit an account from using sudo?

What accout does su map to by default?

Thanks!

---

### Post by deets52 on 2007-09-08
Sorry Aysiu, I posted my response before I saw yours.

Thanks.

---

### Post by deets52 on 2007-09-08
Great information! Thank for the help, that clears up several questions. I do see the waekness in the command, where as if an account is compromised, then root access it granted. With su you would still need the root account's password (unless the root account was the one compromised).

---

