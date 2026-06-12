---
title: "sudo help"
date: 2007-01-20
forum: General Help
---

### Post by Stephen-I-M on 2007-01-20
How can I use sudo so that I don't have to type 'sudo' + command for multiple commands afterwards? Is it 'sudo -' or something like that? Thanks.

Stephen

---

### Post by jimbob on 2007-01-20
sudo su

---

### Post by mcduck on 2007-01-20
Use 'sudo -i' instead of 'sudo su'. 'sudo -i' loads root's environment while other ways to do this use your normal user's environment which may cause some problems. And remember to use 'exit' when you don't need root privileges any more ;)

---

### Post by DerHesse on 2007-01-20
> **mcduck said:**
> Use 'sudo -i' instead of 'sudo su'. 'sudo -i' loads root's environment while other ways to do this use your normal user's environment which may cause some problems. And remember to use 'exit' when you don't need root privileges any more ;)
  or **[CTRL.]+D**

---

### Post by jimbob on 2007-01-20
Is that ctrl key and shift D ?  All at same time ??

---

### Post by cracker on 2007-01-20
No, just control + d. It basically does the exact same thing as typing exit and pressing enter. And yes, sudo -i is the best way to gain a root terminal, as it keeps the security of sudo, and you don't have to set a root password. No root password means no root logins, and far fewer chances of someone compromising you. Of course, if you have a user account with no-password sudo privileges for all commands, then you've defeated the purpose, but I digress.

---

### Post by jimbob on 2007-01-20
Thx ...   :D

---

### Post by Stephen-I-M on 2007-01-22
Actually, I don't want to load root's environment, but my own aliases, vim settings, etc. Is there a version of sudo-something that keeps the user's environment?

Stephen

---

### Post by bodhi.zazen on 2007-01-22
> **Stephen-I-M said:**
> Actually, I don't want to load root's environment, but my own aliases, vim settings, etc. Is there a version of sudo-something that keeps the user's environment?

Stephen

I am not sure, why not try:

sudo su

But I think this will be partial at best.

```
sudo -i
source /home/your_user_name/.bashrc
```

Or wherever you keep your aliases.

Also, you could add a .bashrc to /root

---

