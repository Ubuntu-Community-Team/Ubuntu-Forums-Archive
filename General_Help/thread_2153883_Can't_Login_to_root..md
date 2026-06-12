---
title: "Can't Login to root."
date: 2013-06-12
forum: General Help
---

### Post by seedeh on 2013-06-12
I just installed Ubuntu Desktop 13.04 on to my laptop. The problem is that neither can I access my account, I can't gain root access. I have tried to change the password of my account and root but it has failed. Thanks, seedeh.

---

### Post by Toz on 2013-06-12
Hello and welcome to the forums.

The root account is locked by default in Ubuntu. Have a look [here]("https://help.ubuntu.com/community/RootSudo") for a detailed explanation plus information on how to perform administrative tasks using sudo, gksudo and friends.

---

### Post by Bashing-om on 2013-06-12
seedeh; Hi ! My welcome to the forum.
This tutorial;
Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[INDENT=2]
We are here to help

[/INDENT]

---

### Post by seedeh on 2013-06-12
I already tried to change the password, and it wasnt just root I couldnt access

---

### Post by lisati on 2013-06-12
Some more information might be helpful, such as examples of error messages you're getting when you're trying to log in.

---

### Post by steeldriver on 2013-06-12
If you didn't set a root password, then you should be able to reset your primary sudo account's password from the recovery console by following these instructions

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If it doesn't work, then you'll get better help if you post back exactly what point it is failing at, and any error messages you receive

---

### Post by HiImTye on 2013-06-12
the preferred method of escalating in Ubuntu is using ```
sudo command
```
or, for graphical programs (very important, so as not to change permissions on your user's files)```
gksudo command
```in both cases it will be your administrator's account (the account you created when you installed, as well as anyone added to the admin group) password, not root's password. if you enabled root's password, here's how to disable it, and the rest of the policy, as well as the proper way to gain a root shell without enabling root's account are also located in the following link
[https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account](https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

