---
title: "Disabling password"
date: 2022-12-31
forum: General Help
---

### Post by john-falk on 2022-12-31
[https://askubuntu.com/questions/1102368/how-to-disable-the-login-password-for-a-specific-user](https://askubuntu.com/questions/1102368/how-to-disable-the-login-password-for-a-specific-user)

---

### Post by VMC on 2022-12-31
Privacy > Screen

---

### Post by deadflowr on 2022-12-31
Settings > Privacy > Screen doesn't really have an option to disable the password prompt.
Might be able to set the user to the nopasswdlogin group, but i think Ubuntu login manager gdm needs you to edit a file to allow that.
It's something like /etc/pam.d/gdm-password
You add the line
```
auth sufficient pam_succeed_if.so user ingroup nopasswdlogin
```

When done correctly it should allow you to login by only pressing enter.
(Though I am not sure if it works for logging back in from the lock screen)
More information here: [https://ubuntuhandbook.org/index.php/2019/02/enable-passwordless-login-ubuntu-18-04/]("https://ubuntuhandbook.org/index.php/2019/02/enable-passwordless-login-ubuntu-18-04/")

Issues that come from doing this are
1) The system is now open for anyone to login and mess it up.

2) Normal login with password unlocks the keyring, but using the nopasswdlogin [s]does[/s] might not.
This can be annoying if you use anything that wants the keyring unlocked, 
as you will get a prompt to unlock it whenever the first app that wants to use it is opened.
(Luckily, it only needs to be unlocked once per session)

---

### Post by VMC on 2022-12-31
I just suspended, and on wake up no password required. Went straight to desktop, fully awake

---

### Post by john-falk on 2022-12-31
Thanks!

---

