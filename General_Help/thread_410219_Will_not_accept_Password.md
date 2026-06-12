---
title: "Will not accept Password"
date: 2007-04-15
forum: General Help
---

### Post by Pal369 on 2007-04-15
I installed Ubuntu 6.06.1 LTS, when I try to log on, it will my log in name, BUT it will not accept anything on the "password line". The courser just flashes on the first spot.

How can I fix this?

Thank you.

---

### Post by jeffathehutt on 2007-04-15
Ubuntu (and Linux in general) does not show anything when you type in your password.  Just type your password, hit enter, and you will be logged in.

---

### Post by tgm4883 on 2007-04-15
This is by design a security feature.  Your password is being entered when you type, it just doesn't show on the line (so anyone over your shoulder cannot see the length of your password.)

Just type your password in and hit enter

---

### Post by Pal369 on 2007-04-15
Thank you for your help, but all I get is login incorrect, I may have not done or written down all my Information. Do I need to start all over or can I do it an easier way?

Thank again for the feed back

---

### Post by jeffathehutt on 2007-04-15
Make sure you are using the correct username and password.  Remember that Linux is case sensitive, so 'PASSWORD' is not the same as 'password'

If you just installed Ubuntu and still can't get logged in, it might be easiest to just reinstall it and make sure you typed your password correctly.

---

### Post by aysiu on 2007-04-15
You don't have to reinstall to reset your password.

Reboot. Instead of selecting the regular boot option, press the down arrow once and select *recovery mode*.

When you get to the command prompt root@ubuntu:~$, type ```
passwd pal369
reboot
``` The first command will allow you to reset your password. Be careful when you type. As jeffathehutt mentioned, passwords are case-sensitive.

---

### Post by bapoumba on 2007-04-15
> **Pal369 said:**
> I installed Ubuntu 6.06.1 LTS <snip>
> **Pal369 said:**
> ... but all I get is login incorrect,...

Did you ever log in after the install?
If not, you may have installed with "alternate" version. Your login is then oem, and the password the one you gave during the install.
When logged in, open a terminal (> Accessories > Terminal) and run:
```
sudo oem-config-prepare
```
Next reboot, you will be prompted to create a new user login and a new password and the oem temporary user will the be removed.

---

### Post by jeffathehutt on 2007-04-15
> **aysiu said:**
> You don't have to reinstall to reset your password.

aysiu is absolutely right.  The only reason I suggested a reinstall is because it is possible to mistype the username when you install.  If I remember correctly, you only type the username once, where you type the password twice to confirm it.  If you did in fact mistype the username, it's probably better to reinstall than to try to fix it since you have no data or settings saved.

---

### Post by aysiu on 2007-04-15
Ah, but even if you forgot your username or mistyped it, you could create a new one.

In recovery mode: ```
adduser *username*
adduser admin
reboot
```

---

### Post by jeffathehutt on 2007-04-15
Heh... just ignore me for a while, I'm a bit tired :) 

Listen to aysiu or bapoumba, that would be the best option :D

---

