---
title: "Sudo Error!"
date: 2006-08-26
forum: General Help
---

### Post by taekwondodogoof on 2006-08-26
Hi, whenever I try to run synaptic package manager or updates nothing happens. When I try manual updates, I get this error.

```
jared@MeinKampf:~$ sudo apt-get update
sudo: /etc/sudoers is mode 0777, should be 0440
```

How do I fix this? I think it's a permissions error, but I'm still fairly new at this hole Ubuntu/Linux thing! Thanks for the help :) !

Jared

---

### Post by aysiu on 2006-08-26
Reboot into recovery mode and type these commands: ```
chmod 0440 /etc/sudoers
reboot
```

---

### Post by taekwondodogoof on 2006-08-26
Quick question, sorry for being so ignorant, but how do you boot into recovery mode? And thanks for the help

---

### Post by aysiu on 2006-08-27
Read this (just the part about recovery mode):
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by taekwondodogoof on 2006-08-27
Thanks a ton Aysiu! It worked! Thanks again =D!
          Jared

---

