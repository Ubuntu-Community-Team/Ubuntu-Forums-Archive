---
title: "Ubuntu19xx, User Password, stop it from asking for User Password,"
date: 2020-04-08
forum: General Help
---

### Post by mawil10132 on 2020-04-08
Ubuntu 19xx
How do I stop the common User password request after screen time out or after start up.   Not admin password.

I'm about to wipe and reinstall!  I've performed numerous search online line and here and cannot find anything the works.

The suggestion of clicking on Activities then typing User's then autosign does not work.

---

### Post by yancek on 2020-04-08
Have you tried the method at the end of the post at the link below?

[https://askubuntu.com/questions/1029696/disable-password-request-from-from-suspend-18-04](https://askubuntu.com/questions/1029696/disable-password-request-from-from-suspend-18-04)

---

### Post by uRock on 2020-04-08
Keep in mind that reinstalling and setting to autologin will cause rampant pop-ups for keychain passwords. The time used for reinstalling will be equivalent to typing your password how many times? 

[Disabling screenlock password is simple.]("https://websiteforstudents.com/disable-turn-off-ubuntu-18-04-lts-beta-lock-screen/")

---

### Post by mawil10132 on 2020-04-09
> **yancek said:**
> Have you tried the method at the end of the post at the link below?

[https://askubuntu.com/questions/1029696/disable-password-request-from-from-suspend-18-04](https://askubuntu.com/questions/1029696/disable-password-request-from-from-suspend-18-04)


I did this so far and now get keyring!  So apparently the jokes on me, why this youtuber didn't follow through with a complete solution?

First step to stop being asked for passwords;  ( [https://www.youtube.com/watch?v=2nJebclpQWc](https://www.youtube.com/watch?v=2nJebclpQWc) )

Open terminal > enter; sudo visudo> enter password> enter in two spots; NOPASSWD: ALL, control X, Yes, Enter

SO, This worked sort of, As I'm not being asked for the password after start up, that password screen is gone only to be replaced with another request for password.

> Enter password to unlock

> An application wants access to 

>the keyring "Default keyring" but

>it is locked.

Sooo, now whats going on? How do I fix this so it isn't asking for a password?

---

### Post by mawil10132 on 2020-04-09
> **uRock said:**
> Keep in mind that reinstalling and setting to autologin will cause rampant pop-ups for keychain passwords. The time used for reinstalling will be equivalent to typing your password how many times? 

[Disabling screenlock password is simple.]("https://websiteforstudents.com/disable-turn-off-ubuntu-18-04-lts-beta-lock-screen/")

I am finding this out the hard way, apparently this youtuber posted a partial fix, as as you say KEYRING passwrod now being asked for, soo, I guess I will undo his suggestion and try the one you presented.

Here's what I did,

First step to stop being asked for passwords;  ( [https://www.youtube.com/watch?v=2nJebclpQWc](https://www.youtube.com/watch?v=2nJebclpQWc) )

Open terminal > enter; sudo visudo> enter password> enter in two spots; NOPASSWD: ALL, control X, Yes, Enter

SO, This worked sort of, As I'm not being asked for the password after start up, that password screen is gone only to be replaced with another request for password.

> Enter password to unlock

> An application wants access to 

>the keyring "Default keyring" but

>it is locked.

Sooo, now whats going on? How do I fix this so it isn't asking for a password?   I undid NOPASSWORD: ALL and still get keyring password request,   I'm thinking I just need to reinstall Ubuntu!?

---

### Post by mawil10132 on 2020-04-09
> **uRock said:**
> Keep in mind that reinstalling and setting to autologin will cause rampant pop-ups for keychain passwords. The time used for reinstalling will be equivalent to typing your password how many times? 

[Disabling screenlock password is simple.]("https://websiteforstudents.com/disable-turn-off-ubuntu-18-04-lts-beta-lock-screen/")
That link is obsolete for U19xx, that icon is gone and clicking on the set up icon doesn't bring up that Privacy screen at all.    I undid NOPASSWD: ALL, still get keyring password, Also followed your suggestion still get keyring password request,  I'm real close to reinstalling Ubuntu from scratch...

---

### Post by CelticWarrior on 2020-04-09
Reinstalling and setting autologin will get you to the exact same place. The best practice and also now standard across all major families of OSes is login with a password. So, do the smart thing and save yourself time and money.

---

