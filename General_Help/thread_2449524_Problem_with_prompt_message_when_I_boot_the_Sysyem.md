---
title: "Problem with prompt message when I boot the Sysyem"
date: 2020-08-28
forum: General Help
---

### Post by plutobuntu on 2020-08-28
I believe this started when I installed the email client "Geary", and it asked me to set a password, and I did it without giving it much thoght.

I've tried uninstalling Geary, but the prompt still shows up every time I boot.

It says: "unblock deposit" below: "introduce password to unlock it" and below the main text: "An app wants access to the password deposit "deposit of default passwords" but it is blocked".

Then I have two choices if I want the window to go away: I enter the password, or I close it 3 times...

But I want to disable it and never see it appear again, how could I do that?

---

### Post by ajgreeny on 2020-08-28
What password is being asked for, your user password that you set when installing the OS or your email password that you entered when using geary for the first time?

I haven't used geary for many years but I wonder if you purged it or just removed it?
If you simply removed it there may be some retained configuration that is asking for a password simply because it does not know the the application is now uninstalled.

See if ***sudo apt purge geary*** gets rid of this password request.

---

### Post by plutobuntu on 2020-08-28
> **ajgreeny said:**
> What password is being asked for, your user password that you set when installing the OS or your email password that you entered when using geary for the first time?

It asks me for a password that I had to make for this app, different from the one that I have for the email and as far as I can tell it's different from the one set for the OS (even tho they're both the same, I chose the same to remember it more easily).

> **ajgreeny said:**
> I haven't used geary for many years but I wonder if you purged it or just removed it?
If you simply removed it there may be some retained configuration that  is asking for a password simply because it does not know the the  application is now uninstalled.

See if ***sudo apt purge geary*** gets rid of this password request. 

I tried doing this, but it didn't work.

---

### Post by CelticWarrior on 2020-08-28
Are you using auto-login?

---

### Post by plutobuntu on 2020-08-28
> **CelticWarrior said:**
> Are you using auto-login?

What is "auto-login"? If it means that the system doesn't ask for my admin password after I turn on the pc then yes.

---

### Post by CelticWarrior on 2020-08-28
That is auto-login and the cause of your "problem".
The program asked for a password to unlock the passwords keyring from which it retrieves the stored passwords for your email accounts.

Just don't, not a good practice.

---

