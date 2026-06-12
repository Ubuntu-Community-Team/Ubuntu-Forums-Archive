---
title: "[SOLVED] super user help"
date: 2008-06-13
forum: General Help
---

### Post by slayerkiller on 2008-06-13
I am trying to install some updates and it gives me a prompt stating to run a string in the prompt terminal, once into the terminal I type it in and it says "must be super user" how do I make myself a superuser?? I tried /su and then it ask for a password, I put in my password and it dosent work.

---

### Post by Ender305 on 2008-06-13
super user basically means root privileges, you can use "sudo [command]" and then enter your password or you can use su to log into the terminal as root, but you have to enter the root password, not yours

---

### Post by tamoneya on 2008-06-13
in ubuntu the root account is locked by default.  Instead you should just preceed your commands with sudo.  This will give you super user access for just one command. eg instead of ```
apt-get update
``` you should use```
sudo apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by slayerkiller on 2008-06-13
Thanks I will do that :) also for some reason it wont save my internet settings, I alwayshave to go back and retype everything for it to connect. Is there any way around this. and yes I am a linux noob :P but I do like it so far :)

---

