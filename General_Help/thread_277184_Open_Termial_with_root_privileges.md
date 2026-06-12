---
title: "Open Termial with root privileges"
date: 2006-10-14
forum: General Help
---

### Post by dontgetshocked on 2006-10-14
This OS is very frustrating, how do I open terminal with root privileges so I can run a command that needs root privileges? Do I have to logon as root and if so how? 

Signed new user (frustrated)

---

### Post by CatKiller on 2006-10-14
You can run commands that require root privileges in a normal terminal. Just precede the command with "sudo". These pages may give you more information:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aliyanage on 2006-10-14
Hi,

first you'll have to assign a root password. Open the terminal and do this command: sudo passwd root

then just set the root password and retype it again.
After that you should be able to "su" and then enter root password that you assigned and there you go...

login as root:
if you want to login as root when you boot ubuntu then you'll have to enable that. Go to Systems/Administration/Login Window. Then go to the security tab and Allow system local administrator to login. That way you should be able to have root priv right away when you open terminals...

cheers aliyanage

---

### Post by PriceChild on 2006-10-14
> **aliyanage said:**
> first you'll have to assign a root password. Open the terminal and do this command: sudo passwd rootThis is HIGHLY unreccomended and has been disabled by default in ubuntu as a security feature.

Read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There is no operation which should require the enabling of the root password.

If sudo is not enough, and you need a root terminal, type
```
sudo su -
```

---

### Post by alecjw on 2006-10-14
Or, add to the menu a "gksudo gnome-terminal" option.

---

### Post by bobosity on 2006-10-14
Applications>>System Tools>>Root Terminal.

If it's not there you can install it through synaptic.

---

### Post by alecjw on 2006-10-14
> **bobosity said:**
> Applications>>System Tools>>Root Terminal.

If it's not there you can install it through synaptic.

You don't need to install it, just run the terminal with gksudo.

---

### Post by dcstar on 2006-10-15
> **alecjw said:**
> Or, add to the menu a "gksudo gnome-terminal" option.

I use:
```
gksu /usr/bin/x-terminal-emulator
```

---

### Post by aliyanage on 2006-10-15
also what you can do if you dont want to assign a root passwd just use the sudo -s command when you first log in and that should do it for the terminal. That way you save yourself the sudo part...

---

