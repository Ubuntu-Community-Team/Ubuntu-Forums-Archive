---
title: "Fictitious password"
date: 2012-10-28
forum: General Help
---

### Post by Rabouni on 2012-10-28
Hello,

When I installed ubuntu 12.04 LTS, I carefully chose a login and password. A few weeks ago, I removed my password (setting All Settings, Login Options, "Password" to "None" and "Automatic Login" to "ON").

Since then, whenever I need autorization to execute an action (any updates requires authorization), I am asked for my password. The previous password is not working, nor is a blank password.

However, when I switch to console mode (via the <ctrl><alt><F1> command), the system only asks me for my login, not for my inexisting password, even when I'm executing commands with "sudo".

---

### Post by zombifier25 on 2012-10-28
A user (or the only user) with admin rights should never change his/her password to empty. I have seen far too many cases of people doing this and messing up their system. If you only need automatic login, then you don't need to disable your password.

(also, system updates that does not require the installation/removal of packages don't need to be authenticated)

You can change your password back with the command:
```
sudo passwd username
```

---

