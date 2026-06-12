---
title: "How do I stop Ubuntu asking me to sign in keyring every boot"
date: 2021-04-30
forum: General Help
---

### Post by cheapodonuts on 2021-04-30
As per title. A few months ago, after an update, my pc started asking me to sign in to keyring. 
This machine was Ubuntu from new build. A local business built it for me last year and I asked for it to be set to boot without needing password input. No one else uses it.

So is there anything I can do apart from re-installing the system? I'm gonna buy a Groovy Gorilla USB stick right now anyway, as I always like to pay for the system upgrades that way.

Thanx for any help you guys. &#128513;

---

### Post by CelticWarrior on 2021-04-30
It's either typing your password at the login or later whenever any process needs access to the keyring. So, it's much better - and is what the "bast practices" say - to not have autologin and always type a paasword at the beginning.

---

### Post by cheapodonuts on 2021-04-30
I don't really see why it's much better, it would be ok  by me if it was automatic from startup.
I'm not interested in best practices, they are irrelevant to my situation. No one else is here, I just want my pc to work after I come home from work. I'm 67, and this is my leisure time,  &#9749; &#55356;&#57200; &#9749; &#55358;&#56774; &#9749; &#55358;&#56680; &#9749; &#55356;&#57164; &#9749; &#9749; 
 Ubuntu has apparently altered my system settings without asking me if it's ok. It's not ok, so I want to change it back.

---

### Post by tea for one on 2021-04-30
> **cheapodonuts said:**
> I don't really see why it's much better, it would be ok  by me if it was automatic from startup.
I'm not interested in best practices, they are irrelevant to my situation. No one else is here, I just want my pc to work after I come home from work. I'm 67, and this is my leisure time,  &#9749; &#65533;&#65533; &#9749; &#65533;&#65533; &#9749; &#65533;&#65533; &#9749; &#65533;&#65533; &#9749; &#9749; 
 Ubuntu has apparently altered my system settings without asking me if it's ok. It's not ok, so I want to change it back.

CelticWarrior is correct, autologin should be discouraged. The keyring will be more of an irritation than typing a password at log-in. 

Why not set up a short password? Your leisure time will not be compromised by spending a few seconds typing a password.

---

### Post by cheapodonuts on 2021-04-30
But why did it alter my settings?

---

### Post by tea for one on 2021-04-30
Difficult to answer - probably one of the security updates? 

Anyway, you will find that users who log in with a password (even if it is short) rarely complain about keyring problems.

---

### Post by cheapodonuts on 2021-04-30
Well I suppose I'll accept it for now, but I'll be grumpy about t!
&#128513;&#128513;&#128513;&#128513;&#128513;&#128513;&#128513;&#128513;&#128513;&#128513;

---

### Post by wildmanne39 on 2021-04-30
Hello cheapodonuts, in the future please use the report button in the lower left had corner of the post to politely ask for your post to be removed instead of deleting the content of your post.

Thanks

---

### Post by grahammechanical on 2021-04-30
> Ubuntu has apparently altered my system settings without asking me if it's ok. It's not ok, so I want to change it back.

No. That is not the case. Your system settings are still the same. When you automatically login you should then open Passwords and Keys. Enter your user password in that utility and the system will stop nagging you for a password until the next time you automatically login.

This link explains what is happening and why. What you are seeing is a security feature.

[https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/)

Regards

---

### Post by cheapodonuts on 2021-05-01
Ok boss, :)
  I've never known of that method of deleting one's own post before. I expected to see an option after clicking the edit post button

---

### Post by VMC on 2021-05-02
> **cheapodonuts said:**
> As per title. A few months ago, after an update, my pc started asking me to sign in to keyring. 
...When does it ask for keyring? When you start browser? What are you doing at that moment when keyrings pops up?
I have autologin, and keyring never activates. Are you using Chrome?

---

