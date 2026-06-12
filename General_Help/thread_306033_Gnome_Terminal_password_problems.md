---
title: "Gnome Terminal password problems"
date: 2006-11-24
forum: General Help
---

### Post by wvcaudill2 on 2006-11-24
Hello, I am fairly new to Ubuntu, and it seems im having problems with the terminal. I type in "su" and it asks me for a password. When I try to type in my password, it doesn't do anything. No numbers or letters appear. If I just click enter, it gives me an Authentication Failed error. Please help!

---

### Post by Gustav on 2006-11-24
It's supposed to do that.

Just type your password and then enter.

---

### Post by firebadger on 2006-11-24
su on its own means you are attempting to become root.  You would need to enter the root password and you probably don't have one.  If you want to become root, try sudo su - and type your own password.
However it's better just to run commands with sudo as required rather than becomeing root.

---

### Post by wvcaudill2 on 2006-11-24
Okay, thanks :) Got everything working

---

### Post by Methodize on 2006-12-16
i have the same problem. but nothing shows up as i enter the password. then i hit enter and it just puts me right back where i started.

---

### Post by scrooge_74 on 2006-12-16
In reallity you are not suppose to use the "su" command since the root account is diseable, you should use "sudo" instead and then give your password

---

### Post by majoridiot on 2006-12-18
if you want the equivalent of a root terminal session just:

```
sudo -i
```

and enter your password when prompted

---

