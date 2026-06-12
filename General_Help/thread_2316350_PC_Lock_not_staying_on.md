---
title: "PC Lock not staying on"
date: 2016-03-07
forum: General Help
---

### Post by Camilia on 2016-03-07
I have Ubuntu 15.10 OS. I went to>system>user accounts. Then clicked lock. I shut down the PC. I turn the PC on and no password is asked for. I go to user accounts and see the lock is off. What else can I do to lock the PC?

---

### Post by sotiris2 on 2016-03-08
'Lock' in the User Accounts screens refer to your ability to make changes to users and whether they auto-login or require a password. 

You need to go to User Accounts, unlock (you will need your password) and disable auto-login for any account that has it enabled.

---

### Post by Camilia on 2016-03-08
> **sotiris2 said:**
> 'Lock' in the User Accounts screens refer to your ability to make changes to users and whether they auto-login or require a password. 

You need to go to User Accounts, unlock (you will need your password) and disable auto-login for any account that has it enabled.
I only have 1 user, myself

I would appreciate instructions with your suggestion. 

I have gone to user account clicked the lock and put in my password. I restart and all starts normally without password asked for. I go into my user account and the lock is unlocked. I downloaded users-groups manager. In it I see password is to be asked for but it is not.

---

### Post by QDR06VV9 on 2016-03-08
So this thread shows Solved! Is it Solved...
If it is not there is a method as described below

My fix for that was as follows
```
sudo grep nopasswd /etc/*
```
This will show at least 2 lines like this

```
/etc/group:nopasswdlogin:x:112:`<login name>`   
/etc/gshadow:nopasswdlogin:!::`<login name>`

```
Edit those files with sudo and remove only <login name> from those lines and save.
Go to "User Accounts" and disable the automatic login
Restart the computer and now it should ask for the password again!

---

### Post by Camilia on 2016-03-08
thank got it fixed

---

