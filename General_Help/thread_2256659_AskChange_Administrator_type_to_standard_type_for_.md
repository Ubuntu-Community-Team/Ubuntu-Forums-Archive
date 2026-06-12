---
title: "Ask:Change Administrator type to standard type for account on ubuntu 14.04"
date: 2014-12-14
forum: General Help
---

### Post by n3wguys on 2014-12-14
Hello master,

How to change account privilege type from administrator to standard of type on Ubuntu 14.04 without add new account with standard privilege.. I would like to change it and give limited access to everybody in our machine.

thanks for your help.

---

### Post by deadflowr on 2014-12-14
If you only have one account don't change it, but when adding a new account, it'll automatically set those up as standard.
You should always keep one as an admin, or else if problems happen you won't be able to do anything.

But for what it is worth, open system settings > user account. click on the lock in the top right corner of the window, enter the password for the user, then you can toggle the Account type.

---

### Post by n3wguys on 2014-12-14
Dear Admin,

Normally I was set su password on our system (ubuntu 14.04), and of course I do not have again administrator type in this account. when I had two account, Just all to standard type,when I want to install or prepare, I only go to terminal and access su, so our client need not install their self, they need or face some problem, they only contact their administrator.


> But for what it is worth, open system settings > user account. click on the lock in the top right corner of the window, enter the password for the user, then you can toggle the Account type. 

When I access setting password on account, there I can't see menu of change of type.[ATTACH=CONFIG]258583[/ATTACH]

Is there no ways to do except I have to new account again?
Thanks

---

### Post by grahammechanical on 2014-12-14
When we click to Add a user we get the opportunity to set that user as either Standard or Administrator. As already mentioned, when there is only one user that user is the Administrator and although we can change the password for the Administrator and create other Administrator accounts I do not think we can change the single Administrator account to a standard one without the existence of another Administrator account.

You can try creating a standard user and then try removing the Administrator account. I do not know if that is possible as doing so would make the OS impossible to administer. If we do not have at least one Administrator account would could not create new users or change passwords. We will not be able to authenticate certain system updates.

Regards.

Regards.

---

### Post by deadflowr on 2014-12-14
> **n3wguys said:**
> Dear Admin,

Normally I was set su password on our system (ubuntu 14.04), and of course I do not have again administrator type in this account. when I had two account, Just all to standard type,when I want to install or prepare, I only go to terminal and access su, so our client need not install their self, they need or face some problem, they only contact their administrator.




When I access setting password on account, there I can't see menu of change of type.[ATTACH=CONFIG]258583[/ATTACH]

Is there no ways to do except I have to new account again?
Thanks

You've gone a bridge too far.;)

When you open the user account page and choose the existing account, look at the Line right under the name that says "Account". It should say Administrator. You click on that (The word Administrator) and from there you can toggle it to Standard.

---

### Post by n3wguys on 2014-12-15
Dear All Master,

Thanks for your suggest, I guest no choice to do to downgrade type of account ("standard") when I had "one account" only and there was setting up to administrator(automate by system). I must created one account again to setting up as standard.

Anyway thank you so much.

---

### Post by deadflowr on 2014-12-15
You can still change the account from admin to standard via command line
```
deluser <usernamehere> sudo
```
Change <usernamehere> to what the username is, do not use the < > symbols.
it'll simply remove the user from the sudo group, which is the admin rights group.

---

