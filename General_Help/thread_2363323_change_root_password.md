---
title: "change root password"
date: 2017-06-08
forum: General Help
---

### Post by aminbaik on 2017-06-08
Hello,
if i changed a user  password like root is there an effect on service that is used the account i change it. is  it like a windows that i have the change the password of user in services console ?
thanks.

---

### Post by lisati on 2017-06-08
The "root" account is disabled by default in Ubuntu. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cariboo on 2017-06-09
I'm using Xubuntu here, but go to Users and Groups in system settings to change the password graphically or use the following command in a terminal:

```
sudo passwd username
```

where username is the username you want to change the password for, all you are doing is changing the password and nothing else.

---

### Post by aminbaik on 2017-06-09
> **lisati said:**
> The "root" account is disabled by default in Ubuntu. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

so how I can check the status of root account and the others ?

---

### Post by lisati on 2017-06-09
> **aminbaik said:**
> so how I can check the status of root account and the others ?

Please read the information in the link I provided about the "root" account and gaining admin privileges. 

Changing a user's password should not change their privileges on your system. On my system (plain "vanilla" Ubuntu) users and user groups can be managed by opening "Users and groups."

I see you have started another [thread]("https://ubuntuforums.org/showthread.php?t=2363363") asking about mysql passwords and permissions. Are you asking here about system passwords and permissions, or are you asking about permissions within mysql?

---

